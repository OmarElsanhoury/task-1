
#include <iostream>
#include <string>
#include <cctype>

using namespace std;

string caesarCipher(string text, int shift, string mode = "encrypt") {
    string result = "";
    
    if (mode == "decrypt") {
        shift = -shift;
    }
    
    for (char &c : text) {
        if (isupper(c)) {
            result += char((c + shift - 'A') % 26 + 'A');
        } else if (islower(c)) {
            result += char((c + shift - 'a') % 26 + 'a');
        } else {
            result += c;
        }
    }
    
    return result;
}

int main() {
    string plaintext = "Hello, World!";
    int shift = 3;
    
    string encrypted = caesarCipher(plaintext, shift, "encrypt");
    cout << "Encrypted: " << encrypted << endl;
    
    string decrypted = caesarCipher(encrypted, shift, "decrypt");
    cout << "Decrypted: " << decrypted << endl;
    
    return 0;
}
