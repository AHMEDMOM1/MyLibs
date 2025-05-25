#pragma once

#include <iostream>
#include <iomanip>
#include <cmath>

namespace DataLib { 

	bool include_day_input{ true };
	bool include_month_input{ true };
	bool include_year_input{ true };

	struct Date { 
		short day{};
		short month{};
		short year{};
	};

	enum DateComparisonState {
		Inclusive, 
		Exclusive  
	};

	// Calculates the day of the week (0 = Sunday, 6 = Saturday) using Zeller's congruence.
	short calculate_day_of_week(Date date_info) { 
		int a = (14 - date_info.month) / 12;
		int y = date_info.year - a;
		int m = date_info.month + (12 * a) - 2;
		short d = (date_info.day + y + (y / 4) - (y / 100) + (y / 400) + ((31 * m) / 12)) % 7;
		return d;
	}

	// Prompts user for a positive integer and handles invalid input.
	short get_validated_positive_number(short& num, const std::string& message = "") { 
		std::cout << message;
		while (!(std::cin >> num) || num < 1) {
			std::cin.clear();
			std::cin.ignore(INT_MAX, '\n'); 
			std::cout << "Invalid input. Please enter a positive number: ";
		}
		return num;
	}

	// Fills a Date structure by prompting the user for day, month, and/or year.
	Date get_date_information(bool prompt_day = false, bool prompt_month = false, bool prompt_year = false) { 
		Date date_data{};
		if (prompt_year) date_data.year = get_validated_positive_number(date_data.year, "Enter Year: ");
		if (prompt_month) date_data.month = get_validated_positive_number(date_data.month, "Enter Month: ");
		if (prompt_day) date_data.day = get_validated_positive_number(date_data.day, "Enter Day: ");
		return date_data;
	}

	// Checks if a given year is a leap year.
	bool is_leap_year(short year) { 
		return (year % 400 == 0) || (year % 4 == 0 && year % 100 != 0);
	}

	// Compares two dates and returns true if the first date is earlier than the second.
	bool is_first_date_earlier(Date date1, Date date2) { 
		if (date1.year != date2.year) {
			return date1.year < date2.year;
		}
		if (date1.month != date2.month) {
			return date1.month < date2.month;
		}
		return date1.day < date2.day;
	}

	// Checks if a given date falls on a weekend (Friday or Saturday in your current logic).
	bool is_weekend(Date date_info) { 
		short day_of_week = calculate_day_of_week(date_info);
		return day_of_week == 5 || day_of_week == 6;
	}

	// Gets the number of days in a specific month for a given year.
	short get_days_in_month(short month, short year) {
		if (month == 2)
			return is_leap_year(year) ? 29 : 28;
		else if (month <= 7) // Months 1-7
			return (month % 2 == 0) ? 30 : 31;
		else // Months 8-12
			return (month % 2 == 0) ? 31 : 30;
	}

	// Calculates the total number of days from the beginning of the year to the given date's month and day.
	short calculate_days_from_year_start(Date date_info) { 
		short total_days = date_info.day;
		for (short i = 1; i < date_info.month; i++) {
			total_days += get_days_in_month(i, date_info.year);
		}
		return total_days;
	}

	// Prints a boolean state with a custom message.
	void print_boolean_state(bool state, const std::string& message = "") { 
		std::cout << "Is it " << message << '?' << std::endl;
		state ? std::cout << "Yes, it is " << message << std::endl : std::cout << "No, it isn't " << message << "\n\n";
	}

	// Prints a Date structure in DD/MM/YYYY format.
	void print_date(Date date_info) {
		std::cout << "\n\n" << date_info.day << '/' << date_info.month << '/' << date_info.year << std::endl;
	}

	// Extracts the year from a total number of days (relative to an initial year).
	short get_year_from_days(Date& date_data) { 
		while (date_data.day >= 365) {
			is_leap_year(date_data.year) ? date_data.day -= 366 : date_data.day -= 365;
			date_data.year++;
		}
		return date_data.year;
	}

	// Extracts the month from a remaining number of days within a year.
	short get_month_from_days(Date& date_data) { 
		short current_month = 0;
		short days_in_current_month = 0;
		for (short i = 1; date_data.day > days_in_current_month; i++) {
			date_data.day -= days_in_current_month;
			days_in_current_month = get_days_in_month(i, date_data.year);
			current_month++;
		}
		return current_month;
	}

	// Adds one month to a date, adjusting day if necessary.
	Date add_one_month(Date& date_data) { 
		date_data.month++; // Increment month first to get the next month's days
		if (date_data.day > get_days_in_month(date_data.month, date_data.year)) {
			date_data.day = get_days_in_month(date_data.month, date_data.year);
		}
		if (date_data.month > 12) {
			date_data.month = 1;
			date_data.year++;
		}
		return date_data;
	}

	// Calculates the sum of days between two dates.
	int get_total_days_between_dates(Date start_date, Date end_date, DateComparisonState state = Exclusive) { 
		int total_days_sum = 0;
		// Sum days for full years between start_date and end_date
		for (short y = start_date.year; y < end_date.year; y++) {
			for (short m = start_date.month; m <= 12; m++) {
				total_days_sum += get_days_in_month(m, y);
			}
			start_date.month = 1; // Reset month for the next iteration of years
		}
		// Sum days for months within the end_date's year up to the end_date's month
		for (short m = start_date.month; m < end_date.month; m++) {
			total_days_sum += get_days_in_month(m, end_date.year);
		}
		total_days_sum -= start_date.day; // Subtract days from the start of the start_date's month
		total_days_sum += end_date.day;   // Add days up to the end_date's day

		return (state == Exclusive) ? total_days_sum : total_days_sum - 1; // Adjust based on inclusive/exclusive
	}

	// Adds a specified number of days to a date.
	Date add_days_to_date(Date date_info, short days_to_add) {
		for (int i = 0; i < days_to_add; i++) {
			date_info.day++;
			if (date_info.day > get_days_in_month(date_info.month, date_info.year)) {
				date_info.month++;
				if (date_info.month > 12) {
					date_info.year++;
					date_info.month = 1;
				}
				date_info.day = 1;
			}
		}
		return date_info;
	}

	// Converts a total number of days (relative to an initial year and day) into a Date structure.
	Date get_date_from_days_total(Date date_info) {
		date_info.year = get_year_from_days(date_info);
		date_info.month = get_month_from_days(date_info);
		return date_info;
	}

	// Decreases a date by one month, adjusting day if necessary.
	Date decrease_one_month(Date& date_data) { 
		if (date_data.month == 1) { // If current month is January, go to previous year December
			date_data.month = 12;
			date_data.year--;
		}
		else {
			date_data.month--;
		}

		// Adjust day if it exceeds the number of days in the new month
		if (date_data.day > get_days_in_month(date_data.month, date_data.year)) {
			date_data.day = get_days_in_month(date_data.month, date_data.year);
		}
		return date_data;
	}

	// Decreases a date by one day.
	Date decrease_one_day(Date& date_data) { 
		date_data.day--;
		if (date_data.day == 0) {
			date_data.month--;
			if (date_data.month == 0) {
				date_data.year--;
				date_data.month = 12;
			}
			date_data.day = get_days_in_month(date_data.month, date_data.year);
		}
		return date_data;
	}

	
	void demonstrate_add_days_feature() { 
		Date user_date = get_date_information(include_day_input, include_month_input, include_year_input); // Use global flags
		user_date.day = calculate_days_from_year_start(user_date); // Convert to total days from year start
		short additional_days = 0;
		additional_days = get_validated_positive_number(additional_days, "Enter additional days to add: "); 
		user_date.day += additional_days; 
		print_date(get_date_from_days_total(user_date)); // Convert back to date and print
	}

	// Gets the name of a month from its number.
	std::string get_month_name(short month_number) { 
		std::string months[]{
			"", "January", "February", "March", "April",
			"May", "June", "July", "August",
			"September", "October", "November", "December"
		};
		if (month_number >= 1 && month_number <= 12) {
			return months[month_number];
		}
		return "Invalid Month"; // Handle out-of-range input gracefully
	}

	// Gets the name of a day from its number (0-6).
	std::string get_day_name(short day_number) { 
		std::string days[]{
			"Sunday", "Monday", "Tuesday", "Wednesday",
			"Thursday", "Friday", "Saturday"
		};
		if (day_number >= 0 && day_number <= 6) {
			return days[day_number];
		}
		return "Invalid Day"; // Handle out-of-range input gracefully
	}

	
	void display_calendar_header(short month_number, short year_number) { 
		std::string days_of_week[]{ "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
		std::cout << "\n\n";
		std::cout << std::setw(18) << std::setfill('_') << std::right << get_month_name(month_number) + " " + std::to_string(year_number)
			<< std::setw(15) << '_' << std::setfill(' ') << std::endl;
		for (short i = 0; i < 7; i++) {
			std::cout << std::setw(5) << std::left << days_of_week[i];
		}
		std::cout << std::endl;
	}

	void display_calendar_body(short first_day_of_month_index, Date date_info) { 
		short days_in_month = get_days_in_month(date_info.month, date_info.year);
		short current_day_counter = 1;

		for (short i = 0; i < 7; i++) { // Print leading empty spaces
			if (i >= first_day_of_month_index) {
				std::cout << std::setw(5) << std::left << current_day_counter++;
			}
			else {
				std::cout << std::setw(5) << ' ';
			}
		}
		std::cout << std::endl;

		// Calculate remaining rows
		// This calculation for 'row' and 'column' seems a bit off for a standard calendar grid.
		// A more robust way is to simply loop until all days are printed.
		while (current_day_counter <= days_in_month) {
			for (short j = 0; j < 7; j++) {
				if (current_day_counter <= days_in_month) {
					std::cout << std::setw(5) << std::left << current_day_counter++;
				}
				else {
					std::cout << std::setw(5) << ' ';
				}
			}
			std::cout << std::endl;
		}
	}

	void demonstrate_calendar_display() { 
		Date date_to_display = get_date_information(false, include_month_input, include_year_input);
		short day_of_week_index = calculate_day_of_week(date_to_display);
		display_calendar_header(date_to_display.month, date_to_display.year);
		display_calendar_body(day_of_week_index, date_to_display);
		std::cout << std::setw(33) << std::setfill('_') << '_' << std::setfill(' ') << std::endl;
	}
}
