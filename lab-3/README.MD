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

