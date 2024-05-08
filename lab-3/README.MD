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




## Task – 4: Padding

### Commands

	# ECB Mode (with AES-128)
	openssl enc -aes-128-ecb -e -in input_file.txt -out encrypted_ecb.txt -K your_key_here
	
	# CBC Mode (with AES-128)
	openssl enc -aes-128-cbc -e -in input_file.txt -out encrypted_cbc.txt -K your_key_here -iv your_iv_here
	
	# CFB Mode (with AES-128)
	openssl enc -aes-128-cfb -e -in input_file.txt -out encrypted_cfb.txt -K your_key_here -iv your_iv_here
	
	# OFB Mode (with AES-128)
	openssl enc -aes-128-ofb -e -in input_file.txt -out encrypted_ofb.txt -K your_key_here -iv your_iv_here

### Discussion

CBC mode requires padding due to its block-based operation, while ECB, CFB, and OFB modes do not require padding because they operate on streams of data or encrypt each byte independently.


## Task - 5: Generating Message Digest

### Commands

	openssl dgst -md5 file.txt
	openssl dgst -sha1 file.txt
	openssl dgst -sha256 file.txt

### Generated Hash

	MD5(file.txt)= 87f3b81f4a97107c8d96949edad5cb3c
	SHA1(file.txt)= 06206c025be2418ae6b7e84ba1a1566fe47decda
	SHA2-256(file.txt)= b3c774635a9389dba59067d2ac36509cd2642f1fd4770947612151134d2fbd0f

## Task – 6: Keyed hash and HMAC

### Commands

	openssl dgst -md5 -hmac "abcdefg" file.txt
	openssl dgst -sha1 -hmac "abcdefg" file.txt
	openssl dgst -sha256 -hmac "abcdefg" file.txt

### HMAC

	HMAC-MD5(file.txt)= ce08588a73ae1c5816be95fec69728ad
	HMAC-SHA1(file.txt)= 863bfd435d6ea3b0a70a1be21c9c902fa8623a09
	HMAC-SHA2-256(file.txt)= 825e8c5a2d184a36558cdb0e990785f975903e67fb21b7027f4f16d34bfab59a


## Task – 7: Keyed hash and HMAC-II

### Commands & Outputs

	# Generate MD5 hash for the original file
	>_ md5sum file.txt
	87f3b81f4a97107c8d96949edad5cb3c  file.txt
	
	# Generate SHA256 hash for the original file
	>_ sha256sum file.txt
	b3c774635a9389dba59067d2ac36509cd2642f1fd4770947612151134d2fbd0f  file.txt
	
	# Generate MD5 hash for the modified file
	>_ md5sum file.txt
	e089ee80ff3cd5c2d8be75b7579b8dd7  file.txt
	
	# Generate SHA256 hash for the modified file
	>_ sha256sum file.txt
	012174b6bd31ef5a7c0e2d8e0746b737445773ef12ab35141861e0db0fb90335  file.txt

### Code to compare H1 & H2

```python
def count_same_bits(hash1, hash2):
    # Convert hexadecimal hash values to binary strings
    bin_hash1 = bin(int(hash1, 16))[2:]
    bin_hash2 = bin(int(hash2, 16))[2:]

    # Make the binary strings equal in length by padding with zeros
    max_len = max(len(bin_hash1), len(bin_hash2))
    bin_hash1 = bin_hash1.zfill(max_len)
    bin_hash2 = bin_hash2.zfill(max_len)

    # Count the number of same bits
    same_bits_count = sum(1 for bit1, bit2 in zip(bin_hash1, bin_hash2) if bit1 == bit2)
    return same_bits_count

# Example usage:
hash1 = "87f3b81f4a97107c8d96949edad5cb3c"
hash2 = "e089ee80ff3cd5c2d8be75b7579b8dd7"

same_bits = count_same_bits(hash1, hash2)
print("Number of same bits:", same_bits)
```

