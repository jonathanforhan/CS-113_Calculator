# CS-113_Calculator

## Usage

```C++
int main()
{
    // print Reverse Polish Notation when parsing and debug info on invalid input
    Calculator calc(CalculatorOpts::ePrintRPN | CalculatorOpts::eDebug);

    int64_t result; // result from evaluation
    bool success;   // error checking the return value

    success = calc.evaluate("-2 ^ {5%3} / [1+4-3] * -3", result);

    // return true on successful evaluation and the result will be stored
    // the calculator respects order of operations
    assert(success && result == -6);
}
```

## Algorithm
I used the *Shunting Yard* algorithm to parse a math expression into *Reverse Polish Notation*
> https://en.wikipedia.org/wiki/Shunting_yard_algorithm

## Error handling
The backend Parser uses exceptions and many don't like exceptions but I did this in C++14 which has less utilities for error handling than C++17 or C++20 (ie no std::optional or std::variant). The evaluate function does return a boolean success value though to make it easier to work with.

## Limitations
Currently it cannot handle floating point as input. This may change in the future.