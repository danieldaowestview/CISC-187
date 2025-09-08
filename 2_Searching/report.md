# Activity 2: Searching

## Code

```cpp
//
// Created by daoda on 9/8/2025.
//

#include "searching.h"

#include <iostream>

using namespace std;

int main() {

    // How many steps would it take to perform a linear search for the number 8 in the ordered array, [2, 4, 6, 8, 10, 12, 13]? - 1 pt
    int numbers[] = {2, 4, 6, 8, 10, 12, 13};
    int steps = 0;
    int numberToFind = 8;
    bool found = false;
    cout << "Linear Search" << endl;
    for (int i = 0; i < sizeof(numbers); i++) {
        if (numbers[i] == numberToFind) {
            found = true;
            cout << "Number of steps to find " << numberToFind << ":  " << steps << endl;
            break;
        }
        steps++;
    }
    cout << "Found: " << found << endl;

    // How many steps would binary search take for the previous example? - 1 pt
    steps = 0;
    found = false;
    numberToFind = 8;
    cout << "Binary Search" << endl;
    int leftIndex = 0;
    int rightIndex = (sizeof(numbers) / sizeof(numbers[0])) - 1;
    while (leftIndex <= rightIndex) {
        int midIndex = (leftIndex + rightIndex) / 2;

        if (numbers[midIndex] == numberToFind) {
            found = true;
            cout << "Number of steps to find " << numberToFind << ":  " << steps << endl;
            break;
        }
        if (numbers[midIndex] > numberToFind) { // If middle number is greater than number to find, than we go left half, shifting indexes accordingly
            rightIndex = midIndex - 1;
        }
        else { // If middle number is less than number to find, we go right half
            leftIndex = midIndex + 1;
        }
        steps++;
    }
    cout << "Found: " << found << endl;


    int numbers2[100000];
    numberToFind = std::size(numbers2) - 1;
    found = false;
    steps = 0;
    cout << "Binary Search on 100,000 size Array" << endl;

    for (int i = 0; i < std::size(numbers2); i++) {
        numbers2[i] = i;
    }

    binarySearch(numbers2, 0, std::size(numbers2), numberToFind, steps, found);
}
```

## Flowchart
None used

## Video
https://www.loom.com/share/edd00d3babf940059a322beec064650e?sid=b87bf324-5d07-4be5-b58e-afd9c37aede8
