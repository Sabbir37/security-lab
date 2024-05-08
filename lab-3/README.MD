# Lab 3 | Symmetric Encryption & Hashing

## Task – 1: AES encryption using different modes

Text File: [sample.txt](https://github.com/Sabbir37/security-lab/blob/main/lab-3/task-01/sample.txt)

### Command 1

	openssl enc -aes-128-cbc -e -in sample.txt -out cipher_aes_128_cbc.bin -K 00112233445566778889aabbccddeeff -iv 0102030405060708

Output File: [cipher_aes_128_cbc.bin](https://github.com/Sabbir37/security-lab/blob/main/lab-3/task-01/cipher_aes_128_cbc.bin)

### Command 2

	openssl enc -aes-128-cfb -e -in sample.txt -out cipher_aes_128_cfb.bin -K 00112233445566778889aabbccddeeff -iv 0102030405060708

Output File: [cipher_aes_128_cfb.bin](https://github.com/Sabbir37/security-lab/blob/main/lab-3/task-01/cipher_aes_128_cfb.bin)

### Command 3

	openssl enc -aes-256-cbc -e -in sample.txt -out cipher_aes_256_cbc.bin -K 00112233445566778889aabbccddeeff -iv 0102030405060708

Output File: [cipher_aes_256_cbc.bin](https://github.com/Sabbir37/security-lab/blob/main/lab-3/task-01/cipher_aes_256_cbc.bin)



## Task – 2: Encryption mode - ECB vs CBC

### Commands

	openssl enc -aes-256-ecb -e -in sample.bmp -out sample_aes_256_ecb.bmp -K 00112233445566778889aabbccddeeff
	openssl enc -aes-256-cbc -e -in sample.bmp -out sample_aes_256_cbc.bmp -K 00112233445566778889aabbccddeeff -iv 0102030405060708


### Observations

* ECB Mode
	- Upon viewing the encrypted image (encrypted_ecb.bmp), it appears as random noise or patterns with no discernible features.
	- No identifiable structures or patterns from the original picture are visible.
	- Each block of the image seems to be encrypted independently, leading to a lack of correlation between adjacent blocks.
* CBC Mode
	- The encrypted image (encrypted_cbc.bmp) also displays as random noise or patterns, similar to the ECB mode.
	- However, the patterns may appear slightly different due to the chaining effect where each block is XORed with the previous ciphertext block before encryption.
	- Like ECB, no meaningful information about the original picture can be derived from the encrypted image.


### Conclusion
* The encrypted images, both in ECB and CBC modes, exhibit characteristics of strong encryption.
* Without the decryption key, it is impossible to recover any meaningful information about the original picture from the encrypted images.
* Encryption serves as a vital tool for protecting sensitive information and maintaining confidentiality, as demonstrated by the inability to discern any details from the encrypted images.

### Attachments

Raw Image: [sample.bmp](https://github.com/Sabbir37/security-lab/blob/main/lab-3/task-02/sample.bmp)

Encrypted Image (ECB Mode): [encrypted_ecb.bmp](https://github.com/Sabbir37/security-lab/blob/main/lab-3/task-02/sample_aes_256_ecb.bmp)

Encrypted Image (CBC Mode): [encrypted_cbc.bmp](https://github.com/Sabbir37/security-lab/blob/main/lab-3/task-02/sample_aes_256_cbc.bmp)




## Task – 3: Encryption mode – corrupted cipher text

- The amount of recoverable information from a corrupted ciphertext depends on the encryption mode used.
- ECB mode offers minimal error diffusion and recovery capabilities, resulting in limited recoverable information.
- CBC mode provides better error diffusion and recovery compared to ECB mode.
- CFB and OFB modes offer superior error correction and isolation capabilities, resulting in potentially higher recoverable information from corrupted ciphertexts.

### Attachments
[Click here...](https://github.com/Sabbir37/security-lab/tree/main/lab-3/task-03)

