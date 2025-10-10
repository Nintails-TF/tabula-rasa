---
title: The Last Dance
date modified: Monday, May 13th 2024, 10:16:02 pm
---

 **CHALLENGE DESCRIPTION**

*To be accepted into the upper class of the Berford Empire, you had to attend the annual Cha-Cha Ball at the High Court. Little did you know that among the many aristocrats invited, you would find a burned enemy spy. Your goal quickly became to capture him, which you succeeded in doing after putting something in his drink. Many hours passed in your agency's interrogation room, and you eventually learned important information about the enemy agency's secret communications. Can you use what you learned to decrypt the rest of the messages?*

We are given two files:
1. source.py
	1. This contains a python script, which has been used to generate the message within out.txt
2. out.txt
	1. The cyphertext that we need to decrypt

First things first, we will want to look at the script:
![[Pasted image 20240513213632.png]]

If we can work our way backwards from the script, we can get the output in plaintext.

First of all, the message has been encrypted in hexadecimal, we can reverse this using:
```Bash
xxd -r -p out.txt # -r tells us to revert the hex into binary, -p makes the text type plain.
Ħn��'��$�1z�C��X��>=��!9���L���W��~�=   ?��n�b�go�`�8��k��
                                                         ��s��{��JB�ϫ�H2�!n����ɺ���vA�ʗ���"������~���.*o}4M���Ü��`�M�ª�2H'�l�gk"�C�▒?bu)�}�sδY��8m��.▒���z���
                                                      ����&#�k)i=��TW�v�~.�l��:�9�                                                                                                       
```

Now we have the bits used in the nonce and some plaintext from the source code. We can make a script to perform an XOR analyse of the plaintext and cyphertext:
```Python
def hex_xor(hex1, hex2):
    min_length = min(len(hex1), len(hex2))
    bytes1 = bytes.fromhex(hex1[:min_length])
    bytes2 = bytes.fromhex(hex2[:min_length])
    xor_result = ''.join(f"{b1 ^ b2:02x}" for b1, b2 in zip(bytes1, bytes2))
    return xor_result


known_plaintext = b"Our counter agencies have intercepted your messages and a lot of your agent's iden>
known_hex = known_plaintext.hex()


encrypted_message = "7aa34395a258f5893e3db1822139b8c1f04cfab9d757b9b9cca57e1df33d093f07c7f06e06bb62936>
encrypted_message_part = encrypted_message[:len(known_hex)]


keystream = hex_xor(known_hex, encrypted_message_part)
print("Keystream:", keystream)


encrypted_flag = "7d8273ceb459e4d4386df4e32e1aecc1aa7aaafda50cb982f6c62623cf6b29693d86b15457aa76ac7e2e>
decrypted_flag_hex = hex_xor(keystream, encrypted_flag)

try:
    
    decrypted_flag = bytes.fromhex(decrypted_flag_hex).decode('utf-8')
    print("Decrypted Flag:", decrypted_flag)
except Exception as e:
    print("Error decoding the flag:", str(e))
    print("Decrypted Flag Hex:", decrypted_flag_hex)

```

Executing this script:
```Bash
python xor.py

Keystream: 35d631b5c13780e74a58c3a2405eddaf93259fcaf73fd8cfa985177387587b5c62b7840b629b1bfc121db00dcd4b9972ec0ebad26a66cbcb1232696996ee14fdbdb4f13f3035e5a8cecc3c3641ffd4904400ec8a8ea7acc939f4c2df13618baff2eca6e87a52cea4a5b73fbbcf10fa93c7434b1b09513fd3f572cda7fdcf8a40f521b6e2c589123c4fa6019a10b5db070273fe63eb7b4f6617074cf4

Decrypted Flag: HTB{und3r57AnD1n9_57R3aM_C1PH3R5_15_51mPl3_a5_7Ha7}

```