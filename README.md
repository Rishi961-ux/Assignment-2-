#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    vector<string> names = {"Aarav", "Vihaan", "Ishita", "Kavya", "Saanvi", "Rohan", "Neha"};

   cout << "Original list of names:" << endl;
    for (const string& name : names) {
        cout << name << endl;
    }


  sort(names.begin(), names.end());

  cout << "\nNames sorted alphabetically:" << endl;
    for (const string& name : names) {
        cout << name << endl;
    }

return 0;
}
