#include <iostream>
#include <vector>
using namespace std;

int fastSearch(const vector<int>& numbers, int valueToFind) {
    int left = 0;
    int right = numbers.size() - 1;

    while (left <= right) {
        int middle = left + (right - left) / 2;

        if (numbers[middle] == valueToFind)
            return middle;
        else if (numbers[middle] < valueToFind)
            left = middle + 1;
        else
            right = middle - 1;
    }

    return -1;
}

int main() {
    vector<int> sortedNumbers = {2, 4, 6, 8, 10, 12, 14, 16, 18};
    int numberToFind = 10;

    int index = fastSearch(sortedNumbers, numberToFind);

    if (index != -1)
        cout << "Found " << numberToFind << " at index " << index << "." << endl;
    else
        cout << numberToFind << " was not found in the list." << endl;

    return 0;
}
