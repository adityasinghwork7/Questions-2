# Questions-2
Questions 2
from datetime import datetime, timedelta

def get_t_minus_2_business_day(input_date=None):
    """
    Calculate T-2 business day from a given date, excluding weekends.
    For Mondays, it returns the previous Thursday.
    
    Args:
        input_date (datetime, optional): Input date to calculate from. 
            If None, uses current date.
    
    Returns:
        datetime: Date object representing T-2 business day
    
    Examples:
        >>> from datetime import datetime
        >>> date = datetime(2024, 2, 12)  # A Monday
        >>> get_t_minus_2_business_day(date)
        datetime(2024, 2, 8)  # Returns previous Thursday
    """
    # Use current date if no input date is provided
    if input_date is None:
        input_date = datetime.now()
    
    # Ensure input is datetime object
    if not isinstance(input_date, datetime):
        raise TypeError("Input must be a datetime object")
    
    # Get day of week (0 = Monday, 6 = Sunday)
    day_of_week = input_date.weekday()
    
    if day_of_week == 0:  # Monday
        # Go back 4 days to get to Thursday
        return input_date - timedelta(days=4)
    elif day_of_week == 1:  # Tuesday
        # Go back 4 days to get to Friday
        return input_date - timedelta(days=4)
    elif day_of_week == 6:  # Sunday
        # Go back 4 days to get to Wednesday
        return input_date - timedelta(days=4)
    elif day_of_week == 5:  # Saturday
        # Go back 3 days to get to Wednesday
        return input_date - timedelta(days=3)
    else:
        # For Wednesday, Thursday, Friday go back 2 business days
        return input_date - timedelta(days=2)
