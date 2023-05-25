
Duration: 1h

## Question: Statistical Analysis of a Dataset

Suppose we want to simulate a large dataset of measurements obtained from a scientific experiment. We model these measurements as a normal distribution of floating-point numbers.

Alright, here is the revised part 1 that forbids the usage of explicit for or while loops:

**Part 1:** Write a C++ program using STL algorithms to generate `data`, a `std::vector<double>` with 100,000 elements. Each element should be a random number drawn from a normal distribution with a mean of 0 and a standard deviation of 1. You can use `std::normal_distribution`, `std::default_random_engine` and `std::generate_n` from the `<algorithm>` library to accomplish this.

Makefile:
```makefile
CXX = g++
CXXFLAGS = -std=c++23 -Wall -c
LXXFLAGS = -std=c++23
OBJECTS = main.o
TARGET = main


$(TARGET): $(OBJECTS)
	$(CXX) $(LXXFLAGS) $(OBJECTS) -o $(TARGET)
main.o: main.cpp 
	$(CXX) $(CXXFLAGS) main.cpp
clean:
	rm -f $(TARGET) $(OBJECTS)
```

Prototypes for this task:

```cpp
std::default_random_engine generator;
std::normal_distribution<double> distribution(mean, stddev);
```

```cpp
OutputIt generate_n(OutputIt first, Size count, Generator gen); // creates count elements using gen function
```

Your code creates a `std::vector<double>` filled with the specified number of normally-distributed random numbers. Remember that you are not allowed to use traditional for or while loops in your code.

Hint: Maximum 4 lines of code, do not think hard!

**Part 2:** Continue with writing a one-liner to compute the mean (average) of the data. You can use the `std::accumulate` function from the `<numeric>` library inside this function. The prototype for `std::accumulate` is:

```cpp
T accumulate(InputIt first, InputIt last, T init); // summation of array
```
Hint: init is added to the sum of array, so you may set it to 0.

**Part 3:** Now compute the standard deviation of the data. You need to use the average variable which is calculated in part 2. Use `std::transform` and `std::accumulate` functions for this task. The prototype for `std::transform` is:

```cpp
OutputIt transform(InputIt first1, InputIt last1, OutputIt d_first, UnaryOperation unary_op); // apply unary_op to input and store in output
```
Hint: For equal length Input and Output, you do not need output argument of `std::transform`. `std` and `avg` are near 0 but not exactly 0.

**Part 4:** Now we want to discard outliers from our data, defined as values that are more than two standard deviations away from the mean:

Use the `std::remove_if` function to remove outliers from the `data` vector inplace. Use a lambda function to define the condition. The prototype for `std::remove_if` is:

```cpp
ForwardIt remove_if(ForwardIt first, ForwardIt last, UnaryPredicate p);
```
Hint: The size of `data` decreases.

**Part 5:** Now calculate `avg` and `std` again using the codes in part 2 and 3. If everything is done correctly, they should equal 0 after removing the outliers.

**Note:** For this entire problem, you must not use traditional for or while loops in your code.
