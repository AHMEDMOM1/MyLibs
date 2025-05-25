

# CPP Utility Libraries Collection

![C++ Utilities Banner](https://img.shields.io/badge/C%2B%2B-Utility%20Libraries-blue?style=for-the-badge&logo=c%2B%2B)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![C++17](https://img.shields.io/badge/C%2B%2B-17-blue)](https://en.cppreference.com/w/cpp/17)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://GitHub.com/YourUsername/cpp-utility-libraries/graphs/commit-activity)
[![Documentation](https://img.shields.io/badge/Documentation-Doxygen-blue.svg)](https://YourUsername.github.io/cpp-utility-libraries)

A collection of high-quality, modern C++ utility libraries designed to simplify common programming tasks with elegant, efficient, and well-documented implementations.

## 📚 Libraries Overview

| Library | Description | Status |
| ------- | ----------- | ------ |
| [DateLib](#datelib) | Comprehensive date and calendar manipulation | ✅ Stable |
| [Future Libraries](#roadmap) | Planned additions to the collection | 🔄 Planned |

---

## 🔍 Features

- **Modern C++ Design**: Utilizing C++17 features for clean, efficient code
- **Header-only Implementation**: Easy to integrate into any project
- **Comprehensive Documentation**: Detailed API documentation with examples
- **Strong Type Safety**: Preventing common errors through design
- **Exception-safe Code**: Robust error handling throughout
- **Cross-platform Support**: Works on Windows, macOS, and Linux
- **No External Dependencies**: Self-contained implementations
- **Unit Test Coverage**: Ensuring reliability and correctness

---

## 🛠️ Installation

### Option 1: Include Headers Directly

This is a header-only library collection. Simply copy the headers into your project and include them:

```cpp
#include "DateLib/DateLib.h"
// Future libraries
// #include "StringLib/StringLib.h"
// #include "MathLib/MathLib.h"
```

### Option 2: CMake Integration

```cmake
# In your CMakeLists.txt
add_subdirectory(path/to/cpp-utility-libraries)
target_link_libraries(your_target PRIVATE cpp_utility_libraries)
```

### Option 3: Package Manager

Coming soon with Conan and vcpkg support.

---

## 📆 DateLib

A comprehensive date manipulation library providing intuitive tools for calendar operations, date arithmetic, and formatting.

### Key Features

- **Date Calculations**: Easily work with date differences, adding days/months/years
- **Calendar Generation**: Create and display monthly calendars
- **Date Validation**: Ensure date correctness and handle leap years properly
- **Day of Week**: Calculate the day of week for any date
- **Date Formatting**: Flexible date representation options
- **Weekend Detection**: Identify weekend dates

### Basic Usage

```cpp
#include "DateLib/DateLib.h"
#include <iostream>

int main() {
    // Create a date
    DateLib::Date today(25, 5, 2025);
    
    // Display formatted date
    DateLib::DateIO::displayDate(today, true);  // Shows: Sunday, 25 May 2025
    
    // Add days to a date
    DateLib::Date futureDate = DateLib::DateManipulator::addDays(today, 45);
    DateLib::DateIO::displayDate(futureDate);  // Shows: 9 July 2025
    
    // Check if date is a weekend
    bool isWeekend = DateLib::DateCalculator::isWeekend(today);
    std::cout << "Is weekend? " << (isWeekend ? "Yes" : "No") << std::endl;
    
    // Generate a month calendar
    DateLib::CalendarGenerator::displayMonthCalendar(5, 2025);
    
    return 0;
}
```

### Advanced Features

- Day of year calculation
- Date range operations
- Date comparison
- Leap year calculation
- Day counting between dates

For complete documentation, see the [DateLib Documentation](docs/datelib.md).

---

## 🚀 Getting Started

### Requirements

- C++17 compatible compiler
- CMake 3.14+ (optional, for building tests)
- Doxygen (optional, for building documentation)

### Building Documentation

```bash
mkdir build && cd build
cmake -DBUILD_DOCS=ON ..
make docs
```

Documentation will be generated in the `build/docs/html` directory.

### Building and Running Tests

```bash
mkdir build && cd build
cmake -DBUILD_TESTS=ON ..
make
ctest
```

---

## 🛣️ Roadmap

Future libraries planned for this collection:

| Library | Description | Status |
| ------- | ----------- | ------ |
| StringLib | String manipulation utilities | 🔄 Planning |
| MathLib | Mathematical operations and algorithms | 🔄 Planning |
| FilesystemLib | File and directory operations | 🔄 Planning |
| ConfigLib | Configuration file parsing and handling | 🔄 Planning |
| LoggingLib | Flexible logging facility | 🔄 Planning |

Have suggestions for new libraries? [Submit an idea](https://github.com/YourUsername/cpp-utility-libraries/issues/new?labels=enhancement&template=library_suggestion.md)!

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

---

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 📞 Contact

Your Name - [@your_twitter](https://twitter.com/your_twitter) - email@example.com

Project Link: [https://github.com/YourUsername/cpp-utility-libraries](https://github.com/YourUsername/cpp-utility-libraries)

---

## 🙏 Acknowledgements

- [C++ Core Guidelines](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)
- [Modern C++ Features](https://github.com/AnthonyCalandra/modern-cpp-features)
- [Google Test](https://github.com/google/googletest)

---

<p align="center">
  <i>Built with ❤️ for the C++ community</i>
</p>
