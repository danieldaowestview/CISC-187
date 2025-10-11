# Activity 5: Hash Tables

## Code

```cpp
#include <iosfwd>
//
// Created by daoda on 10/1/2025.
//
#include <iostream>;
#include <vector>

using namespace std;

int main() {
    int array[] = {200, 400, 100, 50, 350};
    int tableSize = 101;
    cout << "Table size of hash table is " << tableSize << endl;
    cout << "Hashing integers by modulo by tableSize, and then inserting into hashTable" << endl;
    vector<int> hashTable(tableSize, -1); // vector<Type> name(size, initialValue);
    for (int num : array) {
        int index = num % tableSize; // Hash function
        cout << "Hash of " << num << " is " << index << " and inserting at " << index << endl;
        hashTable[index] = num;
    }

    int key = 200;
    cout << "Key to lookup is " << key << endl;
    int index = key % tableSize;
    if (hashTable[index] == key) {
        cout << key << " is in the table at index " << index << endl;
    } else {
        cout << key << " not found" << endl;
    }

    cout << "Hashing names by taking ASCII value of each name, modulo by tableSize, and then inserting into hashTable" << endl;
    string names[] = {"Patrick", "Charles", "Brianna", "Sky", "Daniel", "Kevin", "Susan"};
    vector<string> hashTable2(tableSize, "");
    for (string name : names) {
        int ascii = 0;
        for (char c : name) {
            ascii += (int) c;
        }
        cout << "ASCII / Hash of " << name << " is " << ascii << endl;
        cout << "Insert at " << ascii % tableSize << " index" << endl;
        hashTable2[ascii % tableSize] = name;
    }

    string key2 = "Daniel";
    cout << "Key to lookup is " << key2 << endl;
    int ascii = 0;
    for (char c : key2) {
        ascii += (int) c;
    }
    if (hashTable2[ascii % tableSize] == key2) {
        cout << key2 << " is in the hash table" << endl;
    } else {
        cout << key2 << " not found" << endl;
    }


    return 0;
}
```

## Video
https://www.loom.com/share/ef7f6e31c08e41dbad9f5d08f3075304?sid=e59388a7-f297-4455-a308-7124fd579e35
