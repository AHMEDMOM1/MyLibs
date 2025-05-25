-----

# 🚀 My C++ Utility Libraries

Welcome to the home of my personal collection of C++ utility libraries\! This repository serves as a growing toolkit for various programming tasks, starting with robust date and time manipulation. Designed for clarity, efficiency, and ease of use, these libraries aim to streamline common operations in your C++ projects.

-----

## 📅 DateLibrary: Mastering Dates and Times

The **MyDateLibrary** is your go-to solution for comprehensive date management in C++. It provides a powerful and intuitive `Date` class that encapsulates all the essential functionalities for working with dates, from basic properties to complex calculations.

### ✨ Key Features

  * **Robust `Date` Class:** A well-structured class that stores day, month, and year, with built-in validation to ensure only legitimate dates are created.
  * **Leap Year Detection:** Easily determine if a specific year is a leap year.
  * **Day of Week Calculation:** Accurately calculate the day of the week for any given date using standard algorithms.
  * **Date Arithmetic:** Seamlessly add or subtract days and months from a date, handling month and year rollovers automatically.
  * **Date Comparison:** Determine if one date precedes another.
  * **Days Between Dates:** Calculate the total number of days between any two dates.
  * **Calendar Display:** Generate and display elegant calendar views for any month and year.
  * **Clear Naming & Encapsulation:** Adheres to best practices for C++ design, making the code readable and maintainable.
  * **Comprehensive Error Handling:** Utilizes C++ exceptions to gracefully manage invalid inputs or impossible date operations.

### 🛠️ Getting Started

To use `DateLib` in your project, simply include the `DateLib.h` header file:

```cpp
#include "DateLib.h"

int main() {
    // Example: Create a date
   DataLib::Date today({ 25, 5, 2025 });
   DataLib::print_date(today);

    // Example: Add days
   DataLib::Date futureDate = DataLib::add_days_to_date(today, 100);
   DataLib::print_date(futureDate);
   
   // Example: Display a calendar
   DataLib::demonstrate_calendar_display();
    return 0;
}
```

For more detailed examples and demonstrations of how to use various functionalities, refer to the comments within the `DateLib.h` file itself, or explore the example usage in `main.cpp` (if you create one for demonstrations).

### 🚀 Future Enhancements (Flexible Section)

This section can be easily updated as you add more libraries or features.

We plan to continuously expand this collection with other useful C++ utilities. Keep an eye out for:

  * **String Manipulation Library (`MyStringUtils`):** Functions for common string operations like parsing, formatting, and validation.
  * **Mathematical Utilities (`MyMathLib`):** A collection of advanced mathematical functions and constants.
  * **File I/O Helpers (`MyFileIO`):** Simplified functions for reading from and writing to files.

-----

## 🤝 Contributing

Contributions are always welcome\! If you have suggestions for improvements, new features, or find any bugs, please feel free to open an issue or submit a pull request.

-----

## 📜 License

This project is licensed under the [MIT License](https://www.google.com/search?q=LICENSE) - see the `LICENSE` file for details.

-----

## 🙏 Acknowledgments

  * Inspired by the need for clear, reusable C++ code.
  * Special thanks to online C++ communities and resources for guidance.
