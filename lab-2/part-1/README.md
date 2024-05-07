# Ceaser Cipher

## Code


```cpp
#include<bits/stdc++.h>
using namespace std;

string decode(string cipher, int key)
{
    for(int i = 0; i < cipher.size(); i++){
        cipher[i] = (cipher[i] - 'a' - key + 26) % 26 + 'a';
    }
    return cipher;
}

string encode(string plainText, int key)
{
    for(int i = 0; i < plainText.size(); i++) {
        plainText[i] = (plainText[i] - 'a' + key) % 26 + 'a';
    }
    return plainText;
}

int main()
{
    string cipher;
    cipher = "odroboewscdrolocdcwkbdmyxdbkmdzvkdpybwyeddrobo";
    for(int i = 1; i < 26 ; i++){
        cout << "Key = " << i << " Decoded Text: " << decode(cipher, i) << endl;
    }
    
    // Here key 10 will give the correct plain text
    string plainText = decode(cipher, 10);
    cout << "Decoded Text - " << plainText << endl;
    // Encoding with key 10 the plain text will give the cipher text back
    cout << "Encoded Text - " << encode(plainText, 10) << endl;
    return 0;
}

```

## Output

	Key = 1 Decoded Text: ncqnandvrbcqnknbcbvjaclxwcajlcyujcoxavxdccqnan
	Key = 2 Decoded Text: mbpmzmcuqabpmjmabauizbkwvbzikbxtibnwzuwcbbpmzm
	Key = 3 Decoded Text: laolylbtpzaolilzazthyajvuayhjawshamvytvbaaolyl
	Key = 4 Decoded Text: kznkxkasoyznkhkyzysgxziutzxgizvrgzluxsuazznkxk
	Key = 5 Decoded Text: jymjwjzrnxymjgjxyxrfwyhtsywfhyuqfyktwrtzyymjwj
	Key = 6 Decoded Text: ixliviyqmwxlifiwxwqevxgsrxvegxtpexjsvqsyxxlivi
	Key = 7 Decoded Text: hwkhuhxplvwkhehvwvpduwfrqwudfwsodwiruprxwwkhuh
	Key = 8 Decoded Text: gvjgtgwokuvjgdguvuoctveqpvtcevrncvhqtoqwvvjgtg
	Key = 9 Decoded Text: fuifsfvnjtuifcftutnbsudpousbduqmbugpsnpvuuifsf
	Key = 10 Decoded Text: ethereumisthebestsmartcontractplatformoutthere
	Key = 11 Decoded Text: dsgdqdtlhrsgdadrsrlzqsbnmsqzbsokzsenqlntssgdqd
	Key = 12 Decoded Text: crfcpcskgqrfczcqrqkypramlrpyarnjyrdmpkmsrrfcpc
	Key = 13 Decoded Text: bqebobrjfpqebybpqpjxoqzlkqoxzqmixqclojlrqqebob
	Key = 14 Decoded Text: apdanaqieopdaxaopoiwnpykjpnwyplhwpbknikqppdana
	Key = 15 Decoded Text: zoczmzphdnoczwznonhvmoxjiomvxokgvoajmhjpooczmz
	Key = 16 Decoded Text: ynbylyogcmnbyvymnmgulnwihnluwnjfunzilgionnbyly
	Key = 17 Decoded Text: xmaxkxnfblmaxuxlmlftkmvhgmktvmietmyhkfhnmmaxkx
	Key = 18 Decoded Text: wlzwjwmeaklzwtwklkesjlugfljsulhdslxgjegmllzwjw
	Key = 19 Decoded Text: vkyvivldzjkyvsvjkjdriktfekirtkgcrkwfidflkkyviv
	Key = 20 Decoded Text: ujxuhukcyijxuruijicqhjsedjhqsjfbqjvehcekjjxuhu
	Key = 21 Decoded Text: tiwtgtjbxhiwtqthihbpgirdcigprieapiudgbdjiiwtgt
	Key = 22 Decoded Text: shvsfsiawghvspsghgaofhqcbhfoqhdzohtcfacihhvsfs
	Key = 23 Decoded Text: rgurerhzvfgurorfgfznegpbagenpgcyngsbezbhggurer
	Key = 24 Decoded Text: qftqdqgyueftqnqefeymdfoazfdmofbxmfradyagfftqdq
	Key = 25 Decoded Text: pespcpfxtdespmpdedxlcenzyeclneawleqzcxzfeespcp
	Decoded Text - ethereumisthebestsmartcontractplatformoutthere
	Encoded Text - odroboewscdrolocdcwkbdmyxdbkmdzvkdpybwyeddrobo


## Explanation

The decrypted message using key 10 is `ethereumisthebestsmartcontractplatformoutthere`. Re-encrypting this message with the same key reproduces the original cipher text, confirming the decryption was successful. The decryption of the Caesar cipher through brute force was straightforward due to the limited number of possible keys (26). This project illustrates the inherent weakness of the Caesar cipher against brute force attacks, making it unsuitable for applications requiring secure encryption.



























