# Activity 4a: Sorting II

# Source File Code
```cpp
//
// Created by daoda on 9/12/2025.
//

#include "insertionSort.h"

#include <iostream>
using namespace std;

int main() {

    cout << "Proof that, under the average-case scenario, the insertion sort has a time complexity of O(N^2)" << endl;
    // Let's say we were sorting an int array in ascending order, worst-case scenario is when the int array is in complete descending order,
    // while the best-case scenario is when the array is already in ascending order. An average-case scenario would be between best and worse case,
    // with some numbers being out of place, but not all, let's just say the middle is unorganized
    int numbers[] = {2, 1, 3, 7, 6, 5, 4, 9, 8, 10};
    int steps = 0;
    // For insertion sort, we will print the state of the array with every iteration, to show clear proof of the steps.
    for (int i = 1; i < size(numbers); i++) {
        int key = numbers[i]; // Number we will be "extracting" and comparing with other previous numbers
        // int j = i - 1; // Use with while loop

        // Move elements greater than key one step ahead
        /*while (j >= 0 && numbers[j] > key) { // J can't be negative b/c out of bounds and if the number at previous indexes are greater than extracted number, switch them
            cout << "Shifting " << key << " past " << numbers[j] << endl;
            numbers[j + 1] = numbers[j]; // if the number at previous indexes are greater than extracted number, switch them or "shift" them one over
            j--; // Go down the already sorted numbers to see if extracted number is actually less than one of them, and insert it there
        } */
        int j;
        for (j = i - 1; j >= 0 && numbers[j] > key; j--) { // Loop logic must contain BOTH index j being higher than 0, AND that the current number is GREATER than the "extracted number" for index j to decrement
                steps++; // Add to number of steps for shifting numbers
                cout << "Step " << steps << ": ";
                cout << "Shifting " << key << " past " << numbers[j] << endl;
                numbers[j + 1] = numbers[j]; // if the number at previous indexes are greater than extracted number, switch them or "shift" them one over
        }
        numbers[j + 1] = key; // Insert "extracted" number
        steps++; // Add to number of steps for simply going through the array
        cout << "Step " << steps << ": ";
        printArray(numbers, size(numbers));
    }
    cout << "Array has been sorted" << endl;
    cout << "Insertion Sort on Worst-case scenario" << endl;
    int N = 5;
    int numbersWorst[5] = {5, 4, 3, 2, 1};
    insertionSort(numbersWorst, N);
    N = 10;
    cout << "Insertion sort on Average-case scenario" << endl;
    int numbersAverage[N];
    for (int i = 0; i < N; i++) {
        numbersAverage[i] = rand() % 100;
    }
    insertionSort(numbersAverage, N);
}

```

## Header File Code
```cpp
//
// Created by daoda on 9/12/2025.
//

#ifndef UNTITLED_INSERTIONSORT_H
#define UNTITLED_INSERTIONSORT_H
#include <iostream>
#include <vector>
using namespace std;
void printArray(int numbers[], int size) {
    for (int i = 0; i < size; i++) {
        cout << numbers[i] << " ";
    }
    cout << endl;
}

void insertionSort(int numbers[], int size) {
    int steps = 0;
    int operations = 0;
    // For insertion sort, we will print the state of the array with every iteration, to show clear proof of the steps.
    for (int i = 1; i < size; i++) {
        cout << "Starting at index " << i << endl;
        int key = numbers[i]; // Number we will be "extracting" and comparing with other previous numbers
        // int j = i - 1; // Use with while loop

        // Move elements greater than key one step ahead
        /*while (j >= 0 && numbers[j] > key) { // J can't be negative b/c out of bounds and if the number at previous indexes are greater than extracted number, switch them
            cout << "Shifting " << key << " past " << numbers[j] << endl;
            numbers[j + 1] = numbers[j]; // if the number at previous indexes are greater than extracted number, switch them or "shift" them one over
            j--; // Go down the already sorted numbers to see if extracted number is actually less than one of them, and insert it there
        } */
        int j;
        for (j = i - 1; j >= 0; j--) {
            // Loop logic must contain BOTH index j being higher than 0, AND that the current number is GREATER than the "extracted number" for index j to decrement
            operations++; // Count the comparisons
            cout << "Operation " << operations << ": Comparing " << numbers[j] << " and " << key << endl;
            if (numbers[j] > key) {
                operations++; // Add to number of operations for shifting numbers
                cout << "Operation " << operations << ": ";
                cout << "Shifting " << key << " past " << numbers[j] << endl;
                numbers[j + 1] = numbers[j]; // if the number at previous indexes are greater than extracted number, switch them or "shift" them one over
            } else {
                break; // STOP, FOUND RIGHT SPOT FOR KEY
            }
        }
        numbers[j + 1] = key; // Insert "extracted" number
        steps++; // Add to number of steps for simply going through the array
        cout << "Step " << steps << ": Going to index " << i + 1 << endl ;
        printArray(numbers, size);
    }
    cout << "Array has been sorted" << endl;
    
}

bool containsX(string a) { // Time complexity of this function is O(N), worst-case scenario, has to go through entire string of size N to find X
    bool found = false;
    for (int i = 0; i < a.length(); i++) {
        if (a[i] == 'X') {
            found = true;
        }
    }
    return found;
}

inline bool betterContainsX(string a) { // Time complexity of this function is O(N), worst-case scenario, has to go through entire string of size N to find X
    for (int i = 0; i < a.length(); i++) {
        if (a[i] == 'X') {
            return true;
        }
    }
    return false;
}

#endif //UNTITLED_INSERTIONSORT_H
```

## Flowchart
None used

## Video
https://www.loom.com/share/847b735b86a24d3c92c2f39a9601693e?sid=c8e767c6-8947-4df5-b8a2-9a401a5ba388
