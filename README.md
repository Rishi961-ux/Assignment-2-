#include <iostream>
#include <string>
#include <algorithm>
using namespace std;

int main() {
    string inputText;

   cout << "Enter a sentence with uppercase letters: ";
    getline(cin, inputText);

   string lowercaseText = inputText;
   transform(lowercaseText.begin(), lowercaseText.end(), lowercaseText.begin(), ::tolower);

   cout << "The lowercase version is: " << lowercaseText << endl;

return 0;
}
