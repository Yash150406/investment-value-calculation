# README: Compound Interest Calculator (Recursive Version)

## Overview
This is a C program that calculates the compound interest on an initial investment (principal) over a specified number of years using a recursive function. The program prompts the user to enter the initial investment, annual interest rate, and the number of years for which the investment will grow. It then uses recursion to compute the final value of the investment after applying compound interest over the specified period.

## Features
- **Recursive Calculation**: The compound interest is calculated recursively year by year, with each recursive call applying the compound interest formula.
- **Input Validation**: Ensures that the user inputs valid positive values for the principal, interest rate, and the number of years.
- **User-friendly Interface**: The program guides the user to input necessary information and provides meaningful error messages for invalid inputs.

## How to Use
1. **Input the initial investment (Principal)**: The program will prompt you to enter the principal amount. This should be a positive number.
2. **Input the annual interest rate**: Enter the annual interest rate in percentage. The program will convert it to a decimal value internally for calculation.
3. **Input the number of years**: Enter the number of years for which the investment will grow.

The program will then calculate the compound interest recursively and display the final value of the investment.

## Example
### Input
```
Enter the initial investment (Principal): 1000
Enter the annual interest rate (in percentage): 5
Enter the number of years: 3
```

### Output
```
The investment value after 3 years is: 1157.63
```

## Code Explanation

### Main Function
1. The user is prompted to enter:
   - **Principal** (Initial investment)
   - **Interest rate** (in percentage)
   - **Number of years** (duration of the investment)

2. The interest rate is converted from percentage to a decimal for use in the compound interest formula.

3. The recursive function `calculate_compound_interest` is called with:
   - A pointer to the `amount` to allow modification of the value during recursion.
   - The interest rate (as a decimal).
   - The current year (starting from 1).
   - The total number of years to compute.

4. After recursion completes, the final investment value is printed.

### Recursive Function `calculate_compound_interest`
- **Base Case**: The recursion terminates when the current year exceeds the total number of years.
- **Recursive Case**: The `amount` is updated for each year using the compound interest formula:
  \[
  \text{amount} = \text{amount} \times (1 + \text{rate})
  \]
  Then, the function calls itself to calculate for the next year.

### Input Validation
- **Principal**: Must be a positive number.
- **Interest Rate**: Must be zero or positive.
- **Years**: Must be a positive integer.

## Code

```c
#include <stdio.h>

// This is a recursive function to calculate compound interest
void calculate_compound_interest(double *amount, double rate, int year, int years)
{
    // Base case: stop recursion after the specified number of years
    if (year > years)
    {
        return;
    }

    // To update the amount by applying the compound interest formula for the current year
    *amount = *amount * (1 + rate);

    // To recursively call for the next year
    calculate_compound_interest(amount, rate, year + 1, years);
}

int main()
{
    double principal, rate, amount;
    int years;

    // To input principal amount, annual interest rate, and number of years
    printf("Enter the initial investment (Principal): ");
    if (scanf("%lf", &principal) != 1 || principal <= 0)
    {
        printf("Invalid input! Please enter a positive numeric value for the principal.\n");
        return 1;
    }

    printf("Enter the annual interest rate (in percentage): ");
    if (scanf("%lf", &rate) != 1 || rate < 0)
    {
        printf("Invalid input! Please enter a valid interest rate (0 or positive percentage).\n");
        return 1;
    }

    printf("Enter the number of years: ");
    if (scanf("%d", &years) != 1 || years <= 0)
    {
        printf("Invalid input! Please enter a positive integer for the number of years.\n");
        return 1;
    }

    // Convert the annual interest rate from percentage to decimal
    rate = rate / 100;

    // Start with the initial principal amount
    amount = principal;

    // Call the recursive function to calculate compound interest for the specified number of years
    calculate_compound_interest(&amount, rate, 1, years);

    // Display the final amount after the specified number of years
    printf("The investment value after %d years is: %.2lf\n", years, amount);

    return 0;
}
```

## Requirements
- **C Compiler**: To compile and run this code, you'll need a C compiler like GCC or Clang.
- **Operating System**: This code is platform-independent and should run on any system that supports C.

## Compilation and Execution
1. **Compile** the program using a C compiler:
   ```bash
   gcc -o compound_interest compound_interest.c
   ```

2. **Run** the executable:
   ```bash
   ./compound_interest
   ```

## Error Handling
The program ensures:
- **Valid Principal**: A positive number.
- **Valid Interest Rate**: A non-negative percentage.
- **Valid Years**: A positive integer.

If any invalid input is provided, the program will print an error message and terminate.

## Conclusion
This program is a simple yet effective demonstration of how recursion can be used to calculate compound interest. It also includes basic input validation to ensure that the user provides appropriate values for the principal, interest rate, and number of years.
