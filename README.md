#include <iostream>
#include <string>
#include <algorithm>
using namespace std;

int main() {
    string originalText = "OpenAI";
    string reversedText = originalText;
    reverse(reversedText.begin(), reversedText.end());
cout << "Original string: " << originalText << endl;
    cout << "Reversed string: " << reversedText << endl;

return 0;
}
