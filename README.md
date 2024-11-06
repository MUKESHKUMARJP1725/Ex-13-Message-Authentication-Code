# Ex-13 Message Authentication Code

## Date:

## Aim:

To implement the Message Authentication Code (MAC) for data integrity and authenticity verification.

## Algorithm:

1. Define a secret key shared between sender and receiver.
2. Choose a hash function or block cipher (e.g., HMAC or CBC-MAC).
3. Sender computes the MAC by applying the secret key and hash function on the message.
4. Sender transmits both the message and MAC to the receiver.
5. Receiver computes the MAC on the received message using the same secret key.
6. If the computed MAC matches the received MAC, the message is authenticated

## Program:
```
#include <iostream>
#include <string>

// Simple XOR-based hash function to simulate a MAC
std::string computeMAC(const std::string &message, const std::string &key) {
    std::string mac;
    for (size_t i = 0; i < message.size(); ++i) {
        mac += message[i] ^ key[i % key.size()];  // XOR each character with key
    }
    return mac;
}

void printMAC(const std::string &mac) {
    std::cout << "MAC: ";
    for (unsigned char c : mac) {
        printf("%02x", c);
    }
    std::cout << std::endl;
}

int main() {
    std::string key = "secretkey";
    std::string message = "Important message";
    std::string mac = computeMAC(message, key);
    printMAC(mac);
    return 0;
}
```
## Output:

![image](https://github.com/user-attachments/assets/8aba3da0-e636-42e8-aeee-a494c04bb118)

## Result:
The MAC algorithm is successfully implemented, providing data integrity and authentication.
