#include <iostream>
#include <unordered_set>
using namespace std;

int main() {
    int n;
    cout << "Enter number of elements: ";
    cin >> n;
    int arr[n];
    unordered_set<int> distinct;
    cout << "Enter the elements:\n";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
        distinct.insert(arr[i]);
    }
    cout << "Total distinct elements: " << distinct.size() << endl;

    return 0;
}#include <iostream>
#include <unordered_set>
using namespace std;

int main() {
    int n;
    cout << "Enter number of elements: ";
    cin >> n;

   int arr[n];
    unordered_set<int> distinct;

   cout << "Enter the elements:\n";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
        distinct.insert(arr[i]);
    }

   cout << "Total distinct elements: " << distinct.size() << endl;

    return 0;
}

