#include <iostream>
#include <string>
using namespace std;

bool isVowel(char c) {
    c = tolower(c);
    return (c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u');
}

int main() {
    string inputText;
    string result;

    cout << "Enter a sentence: ";
    getline(cin, inputText);

    for (char c : inputText) {
        if (!isVowel(c)) {
            result += c;
        }
    }

    cout << "Text after removing vowels: " << result << endl;

    return 0;
}
