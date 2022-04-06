import time
import pandas as pd
import numpy as np

CITY_DATA = { 'chicago': 'chicago.csv',
              'new york city': 'new_york_city.csv',
              'washington': 'washington.csv' }

def get_filters():
    """
    Asks user to specify a city, month, and day to analyze.

    Returns:
        (str) city - name of the city to analyze
        (str) month - name of the month to filter by, or "all" to apply no month filter
        (str) day - name of the day of week to filter by, or "all" to apply no day filter
    """
    print('Hello! Let\'s explore some US bikeshare data!')
    # TO DO: get user input for city (chicago, new york city, washington). HINT: Use a while loop to handle invalid inputs
    city = input("Would you like to see data for Chicagago,New York,or Washintog ").lower()
    while city not in CITY_DATA.keys():
        print('Invalid City Please write valid city ')
        city = input("Would you like to see data for Chicagago,New York,or Washintog ").lower()
          
         # TO DO: get user input for month (all, january, february, ... , june)
    global months 
    months = ['january', 'february', 'march', 'april', 'may', 'june','all']
   
    while True :
        month = input("Do you need to filter in month 'january', 'february', 'march', 'april', 'may', 'june' or all months ").lower()
        if month in months:
            break
        else:
            print('Invalid Month ')
           
   # TO DO: get user input for day of week (all, monday, tuesday, ... sunday)
    days = ['all', 'monday', 'tuesday','wodnesday', 'thursday','friday','sunday','saturday']
    while True :
        day = input("In which day do you need to filter or all?: ").lower()
        if day in days:
            break
        else:
            print('invalid day')
            
    print('-'*40)
    return city, month, day
          

def load_data(city, month, day):
    """
    Loads data for the specified city and filters by month and day if applicable.

    Args:
        (str) city - name of the city to analyze
        (str) month - name of the month to filter by, or "all" to apply no month filter
        (str) day - name of the day of week to filter by, or "all" to apply no day filter
    Returns:
        df - Pandas DataFrame containing city data filtered by month and day
    """
    df = pd.read_csv(CITY_DATA[city])
    df['Start Time'] = pd.to_datetime(df['Start Time'])
    df['month'] = df['Start Time'].dt.month
    df['week_day'] = df['Start Time'].dt.weekday
    df['hour'] = df['Start Time'].dt.hour
    
    if month != 'all':
        # use the index of the months list to get the corresponding int
        #months = ['january', 'february', 'march', 'april', 'may', 'june']
        month = months.index(month)+1
        # filter by month to create the new dataframe
        df = df[df['month']==month]
        # filter by day of week if applicable
    
    if day != 'all':
        # filter by day of week to create the new dataframe
        df = df[df['week_day'] == day.title()]
        
    return df


def time_stats(df):
    """Displays statistics on the most frequent times of travel."""

    print('\nCalculating The Most Frequent Times of Travel...\n')
    start_time = time.time()

    # TO DO: display the most common month
    popular_month = df['month'].mode()[0]
    print("The most common month is  "+ str(popular_month))
    
    # TO DO: display the most common day of week
    popular_day = df['week_day'].mode()[0]
    print("The most common day is "+ str(popular_day))
    
    # TO DO: display the most common start hour
    popular_hour = df['hour'].mode()[0]
    print("The most common hour is  "+str(popular_hour))
    
    print("\nThis took %s seconds." % (time.time() - start_time))
    print('-'*40)


def station_stats(df):
    """Displays statistics on the most popular stations and trip."""

    print('\nCalculating The Most Popular Stations and Trip...\n')
    start_time = time.time()
    # End Time (e.g., 2017-01-01 00:20:53)
    # Trip Duration (in seconds - e.g., 776)
    # Start Station (e.g., Broadway & Barry Ave)
    # End Station (e.g., Sedgwick St & North Ave)
    # User Type (Subscriber or Customer)

    # TO DO: display most commonly used start station
    startStation = df['Start Station'].mode()[0]
    print("The most commonly used start station is " +startStation)
    
    # TO DO: display most commonly used end station
    endStation = df['End Station'].mode()[0]
    print("The most commonly used end station is " +endStation)
    
    # TO DO: display most frequent combination of start station and end station trip
    df['combination'] =  df['Start Station'] + ","+df['End Station']
    combination = df['combination'].mode()[0]
    print("the most frequent combination of start station and end station trip is "+ combination)
    
    print("\nThis took %s seconds." % (time.time() - start_time))
    print('-'*40)


def trip_duration_stats(df):
    """Displays statistics on the total and average trip duration."""

    print('\nCalculating Trip Duration...\n')
    start_time = time.time()

    # TO DO: display total travel time
    totalTime = round(df['Trip Duration'].sum(),2)
    print("The Total travel time is : "+ str(totalTime))
    # TO DO: display mean travel time
    meanTime = round(df['Trip Duration'].mean(),2)
    print("The Mean travel time is "+str(meanTime))
    print("\nThis took %s seconds." % (time.time() - start_time))
    print('-'*40)


def user_stats(df,city):
    """Displays statistics on bikeshare users."""

    print('\nCalculating User Stats...\n')
    start_time = time.time()
    # User Type (Subscriber or Customer)
    # TO DO: Display counts of user types
    countOfUserType = df['User Type'].value_counts().to_frame()
    print(countOfUserType)
    # TO DO: Display counts of gender
    if city != 'washington':
        countOfGender = df['Gender'].value_counts().to_frame()
        print(countOfGender)
        # TO DO: Display earliest, most recent, and most common year of birth
        earlistYearOfBirth = int(df['Birth Year'].min())
        recentYearOfBirth = int(df['Birth Year'].max())
        commonYearOfBirth = int(df['Birth Year'].mode()[0])
        print("The earliest year of birth is:" +str(earlistYearOfBirth))
        print("The recent year of birth is:" +str(recentYearOfBirth))
        print("The common year of birth is:" +str(commonYearOfBirth))
    else:
        print("This file haven't birth date  column")

    print("\nThis took %s seconds." % (time.time() - start_time))
    print('-'*40)
def display_raw_data(df):
    """ display data  """
    i = 5
    raw = input("Do you need to display row of data").lower() # TO DO: convert the user input to lower case using lower() function
    pd.set_option('display.max_columns',200)

    while True:            
        if raw == 'no':
            break
        elif raw == 'yes':
            print(df[:i]) # TO DO: appropriately subset/slice your dataframe to display next five rows
            raw = input("Do you need to display row of data ").lower() # TO DO: convert the user input to lower case using lower() function
            i += 5
        else:
            print("Your input is invalid. Please enter only 'yes' or 'no'\n")

def main():
    while True:
        city, month, day = get_filters()
        df = load_data(city, month, day)

        time_stats(df)
        station_stats(df)
        trip_duration_stats(df)
        user_stats(df,city)
        display_raw_data(df)

        restart = input('\nWould you like to restart? Enter yes or no.\n')
        while True:
            if (restart.lower() !='No') and (restart.lower() !='YES'):
                print("In Valid input Please Try Again")
                break
            elif restart.lower() != 'YES':
                break


if __name__ == "__main__":
    main()
