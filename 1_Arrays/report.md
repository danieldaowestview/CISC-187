# Activity 1: Arrays

## Code

```cpp
#include <iostream>
#include <cstdlib>
#include <ctime>

using namespace std;

int main() {
    int numbers[100];

    srand(static_cast<unsigned int>(time(0))); // Seed for random number generation
    // Filling the array with random values 0 to 99
    for (int i = 0; i < 100; i++) {
        numbers[i] = rand() % 100;
    }

    // Operations and their Number of Steps in Big O Notation
    // Reading an Array and Outputting to Console
    // for (int i = 0; i < 100; i++) {
    //    cin >> numbers[i];
    // }
    // Steps: 100 (one for each element) => O(n)

    // Searching for a value not contained in the array
    int searchValue = 101; // Value not in the range 0-99
    bool found = false;
    for (int i = 0; i < 100; i++) {
        if (numbers[i] == searchValue) {
            found = true;
            cout << searchValue << "is in contained within the array" << endl;
            break;
        }
    }
    cout << searchValue << " is not in contained within the array" << endl;
    // Steps: 100 (in the worst case, we check all elements) => O(n)

    // Insertion at the beginning of the array
    numbers[0] = 42; // Example value
    // Steps: 1 (direct access) => O(1)

    // Insertion at the end of the array
    numbers[std::size(numbers) - 1] = 84; // Example value
    // Steps: 1 (direct access) => O(1)

    // Deletion at the beginning of the array
    // You can't really "delete" in a static array, but you can overwrite
    numbers[0] = 0; // Example of overwriting the first element
    // Steps: 1 (direct access) => O(1)

    // Deletion at the end of the array
    numbers[99] = 0; // Example of overwriting the last element
    // Steps: 1 (direct access) => O(1)

    // Searching for and counting every instance of "apple" in an array of n elements
    string fruits[100];
    // Filling the array with random fruits for demonstration
    string sampleFruits[] = {"apple", "banana", "orange", "grape", "pear"};
    for (int i = 0; i < 100; i++) {
        fruits[i] = sampleFruits[rand() % 5];
    }
    string targetFruit = "apple";
    int appleCount = 0;
    for (int i = 0; i < 100; i++) {
        if (fruits[i] == targetFruit) {
            appleCount++;
            cout << "Found apple at index " << i << endl;
        }
    }
    cout << "Total apples found: " << appleCount << endl;
    // Steps: 100 (in the worst case, we check all elements) => O(n)

    // How to find the memory address of an array element in C++
    // By using the & (address-of) operator which gives the address of a variable
    cout << "Address of first element: " << &numbers[0] << endl;
    // or
    // By using the array name which acts as a pointer to the first element
    cout << "Address of first element using array name: " << numbers << endl;
    // Rest of the addresses can be found by incrementing the pointer
    cout << "Address of second element: " << &numbers[1] << endl;
    cout << "Address of third element: " << &numbers[2] << endl;
    // And so on...
    // Addresses increment by 4 bytes for int (on most systems)

    // You can also use pointer to point to array memory locations
    int* ptr = numbers; // Pointer to the first element of the array
    cout << "Address using pointer: " << ptr << endl;
    cout << "Value at pointer: " << *ptr << endl; // Using dereferencing operator (*) to get the value
}
```

## Flowchart
None used

## Video
https://www.loom.com/share/bbb57451d7124f89ad96aa8b3825c570?sid=fe7059a1-2fbd-4dc3-a050-1dd172c89225
