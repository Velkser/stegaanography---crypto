# Steganography with AES Encryption in BMP Images

## Project Overview

This project provides a Python-based solution to hide (encode) and retrieve (decode) encrypted text within BMP images using steganography techniques. The text is first encrypted using **AES (Advanced Encryption Standard)** and then embedded into the image's pixel data by manipulating the least significant bits. The process ensures that the message is secure and hidden within an image file.

## Features

- **AES encryption**: Ensures that the text is encrypted before embedding into the image.
- **Steganography**: Hides encrypted text in a BMP image using configurable bit-level encoding.
- **Customizable encoding degree**: The number of bits used for encoding (1, 2, 4, or 8 bits per byte) can be specified.
- **BMP support**: Works specifically with 24-bit BMP images.
- **Decryption**: Recovers and decrypts the hidden text from the encoded image.

## Requirements

- Python 3.7+
- PyCryptodome library for AES encryption

### Installation

1. Clone the repository:

```bash
git clone https://github.com/username/repository_name.git
cd repository_name
```

2. Install the required dependencies:
```bash
pip install -r requirements.txt
```

### Usage
#### Encoding Text into a BMP Image
To encode a message into a BMP image, the text is encrypted and then hidden within the pixel data of the image. Here's how to use the `encode_image` function:

```python
encode_image('input_image.bmp', 'output_image.bmp', 'message.txt', degree=4)
```

- input_image.bmp: The original 24-bit BMP image.
- output_image.bmp: The image where the message will be embedded.
- message.txt: The text file containing the message to be hidden.
- degree: Number of bits used for encoding the message (1, 2, 4, or 8).

#### Decoding Text from a BMP Image
To decode the hidden message from a BMP image, you need to know the number of symbols to retrieve and the encoding degree:

```python
decode_image('encoded_image.bmp', 'output_message.txt', symbols_to_read, degree=4, symb_count=26284)
```

- encoded_image.bmp: The BMP image with the hidden message.
- output_message.txt: The file where the decoded message will be written.
- symbols_to_read: The number of symbols (characters) to extract.
- degree: The number of bits used for encoding.
- symb_count: Total symbol count to decode.

### Encryption and Decryption
The project uses AES encryption to secure the message before it is hidden in the image. A password-based key derivation function (PBKDF2) is used to create the encryption key from a user-provided password.

- Encryption: The `encrypt_message` function encrypts the message using AES-CBC mode, and the resulting ciphertext is encoded in base64 for easy handling.
- Decryption: The `decrypt_message` function reverses the encryption, recovering the original plaintext from the base64-encoded ciphertext.

#### Encrypting a Message:
```python
cipher_text = encrypt_message("your_secret_message")
```

### Security Considerations
The strength of the encryption depends on the password used. Ensure you use a strong password for key generation.
AES encryption adds an additional layer of security to the hidden message, making it difficult for unauthorized users to retrieve the message without the correct password.


### License
This project is licensed under the MIT License. See the `LICENSE` file for details.

