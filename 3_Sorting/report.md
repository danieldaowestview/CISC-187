# Activity 3: Sorting

## Code

```cpp
//
// Created by daoda on 9/10/2025.
//

#include "sorting.h"

#include <bits/stdc++.h>
using namespace std;

int main() {
    cout << "Time complexity of algorithm that takes N^2 Steps" << endl;
    long long counter = 0;
    clock_t begin = clock();
    int N = 50000; // try adding a few more zero digitS at the back of this variable to make your computer hangs...
    for (int i = 0; i < N; ++i) { // O(c * N*N) = O(cN^2), c is 'small' if you leave line 14 commented, but c is BIG if you uncomment it
        // printf("i = %d\n", i);
        // for (int j = 1; j < N; j*=2) { // O(log N)
        for (int j = 0; j < N; ++j) { // O(N) inner loop, that will be repeated N times in the outer loop
            ++counter; // this operation is O(1), and fast, let's say 0.0000000001 s
            // but if you uncomment the next line, the same algorithm will be noticeably much slower
            // printf(" counter = %d\n", counter); // this I/O operation is 'heavy', let's say 0.01s per statement...
        }
    }
    printf("counter = %lld, computed in = %.12fs\n", counter, (double)(clock()-begin)/CLOCKS_PER_SEC);


    cout << " Time complexity of an algorithm that takes 4N + 16 steps" << endl;
    counter = 0;
    begin = clock();
    for (int a = 0; a < 4; a++) { // O(4N) outer loop, that will be repeated 4 times
        for (int j = 0; j < N; j++) { // O(N) inner loop, that will be repeated N times in the outer loop
            ++counter;
        }
    }
    for (int b = 0; b < 16; b++) { // Additional 16 steps
        ++counter;
    }
    printf("counter = %lld, computed in = %.12fs\n", counter, (double)(clock()-begin)/CLOCKS_PER_SEC);
    cout << "Compare previous algorithm with base O(N) time complexity algorithm" << endl;
    counter = 0;
    begin = clock();
    for (int c = 0; c < N; c++) {
        ++counter;
    }
    printf("counter = %lld, computed in = %.12fs\n", counter, (double)(clock()-begin)/CLOCKS_PER_SEC);
    cout << "Time complexity of an algorithm that takes 2N^2 steps" << endl;
    counter = 0;
    begin = clock();
    for (int d = 0; d < 2; d++) {
        for (int e = 0; e < N; e++) {
            for (int f = 0; f < N; f++) {
                ++counter;
            }
        }
    }
    printf("counter = %lld, computed in = %.12fs\n", counter, (double)(clock()-begin)/CLOCKS_PER_SEC);
    cout << "Time complexity of the following function, which returns the sum of all numbers of an array after the numbers have been doubled" << endl;
    vector<int> numbers(N);
    for (int i = 0; i < numbers.size(); i++) { // Fill numbers array with indexes
        numbers[i] = i;
    }
    vector<int> doubledArray(numbers.size());
    counter = 0;
    begin = clock();
    for (size_t i = 0; i < numbers.size(); i++) { // Takes N steps, size of original numbers array
        doubledArray[i] = numbers[i] * 2;
        counter++;
    }
    int sum = 0;
    for (int i : doubledArray) { // Takes another N steps, therefore overall time complexity if just O(N)
        sum += i;
        counter++;
    }
    cout << "Sum of doubled array: " << sum << endl;
    printf("counter = %lld, computed in = %.12fs\n", counter, (double)(clock()-begin)/CLOCKS_PER_SEC);
    cout << "Time complexity of the following function, which accepts an array of strings and prints each string in multiple cases" << endl;
    counter = 0;
    vector<string> strings(100);
    // Filling the array with random fruits for demonstration
    string sampleFruits[] = {"apple", "banana", "orange", "grape", "pear"};
    for (int i = 0; i < strings.size(); i++) {
        strings[i] = sampleFruits[rand() % 5];
    }
    begin = clock();
    // begin conversions
    // Uppercase
    for (size_t i = 0; i < strings.size(); i++) { // N steps, with N being the size of the array
        std::transform(strings[i].begin(), strings[i].end(), strings[i].begin(), ::toupper);
        cout << strings[i] << endl;
        ++counter;
    }
    // Lowercase
    for (size_t i = 0; i < strings.size(); i++) { // N steps
        std::transform(strings[i].begin(), strings[i].end(), strings[i].begin(), ::tolower);
        cout << strings[i] << endl;
        ++counter;
    }
    // Capitalize
    for (size_t i = 0; i < strings.size(); i++) { // N Steps
        string result = strings[i];
        result[0] = toupper(result[0]); // PS. Time complexity is lower, since we don't need to lowercase the rest of the string because we already did that as a result of the last conversion
        cout << result << endl;
        ++counter;
    }
    printf("counter = %lld, computed in = %.12fs\n", counter, (double)(clock()-begin)/CLOCKS_PER_SEC);
    cout << "Time complexity of function that iterates over an array of numbers, and for each number whose index is even, it prints the sum of that number plus every number in the array." << endl;
    counter = 0;
    sum = 0;
    begin = clock();
    for (size_t i = 0; i < numbers.size(); i++) {
        if (numbers[i] % 2 == 0) {
            sum += numbers[i];
            ++counter;
        }
    }
    printf("Sum of every even number in numbers array = %d, counter = %lld, computed in %.12fs\n", sum, counter, (double)(clock()-begin)/CLOCKS_PER_SEC);
    return 0;
}

// the default setup of this starting SpeedTest.cpp should be around 2-3s
```

## Flowchart
None used

## Video
https://www.loom.com/share/1fc8c919f7f04dd5b48ee3ed63cc56d8?sid=e19ae309-8485-4d96-a6bb-b577c96ef06f
