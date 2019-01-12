# ctf-backup

# Ciphers
Identifying Unknown Ciphers
The scenario: you have an unknown cipher and you need to decipher it. You don't know the key, or even the algorithm that was used to create the ciphertext! What can be done to retrieve the plaintext? This page will lay out some rules for identifying unknown ciphers.

Classes of Cipher Algorithms 
There are several different classes of cipher algorithms, each of which use different methods for jumbling plaintext characters. Some of the classes are as follows:

Transposition ciphers - these involve permuting only the positions of the characters, but leaving the identity of the characters unchanged. examples include Railfence, Columnar Transposition, route ciphers etc.
Monoalphabetic substitution ciphers - each letter is replaced with another. Examples include simple substitution, caesar, affine, trithemius cipher, polybius square, Baconian cipher etc.
Polyalphabetic ciphers - different alphabets are used to encipher letters depending on their position. Examples include Porta cipher, Vigenere, Gronsfeld, Beaufort, Autokey, Running key cipher, and even ciphers such as Enigma.
Polygraphic Substitution ciphers - groups of characters are replaced. Examples include Hill cipher, playfair, foursquare etc.
Other types - these ciphers may include elements from several of the above classes. Examples include bifid, trifid, ADFGVX, Straddle checkerboard etc.
Given that there are so many different ciphers, how can we expect to identify a piece of ciphertext? Different ciphers leave different 'fingerprints' on the ciphertext which we can use. Some of the fingerprints are very faint though. All of the methods explained here need quite a bit of ciphertext, 1000 or more characters is ideal. If all you have is 20 characters there is not much you can do. Very short ciphers may be unbreakable if their length is less than the unicity distance of the cipher used to encipher them.

Initial Questions 
How many different characters are there? If there are only 2 different symbols, it is likely the cipher is Baconian. If there are 5 or 6 it is probably a polybius square cipher of some sort, or it may be ADFGX or ADFGVX. If there are more than 26 characters it is likely to be a code or nomenclator of some sort or a homophonic substitution cipher. If there are around 26 characters, then read on.

If there are 26 characters in the ciphertext, it rules out ciphers based on a 5 by 5 grid such as playfair, foursquare and bifid. If the ciphertext is fairly long and only 25 characters are present, it may indicate a cipher in this class has been used.

The Steps to Take 
Our first step is to try and differentiate between transposition ciphers and all other ciphers. This can be done using monogram frequencies; English text has a very specific frequency distribution that is not changed by transposition ciphers. All other ciphers change this distribution, so the frequencies can be used to differentiate them. If the frequency distribution looks exactly like a piece of english text but it is still unreadable we can conclude it is probably a transposition cipher, otherwise we move onto the next step.

The next step is to determine if the cipher is a substitution cipher of some sort. Here we calculate the Index of Coincidence (I.C.). If the Index of Coincidence is around 0.06 we conclude the cipher is probably a substitution cipher. If it is lower, it is most probably some sort of polyalphabetic, polygraphic or more complex cipher.

If it is a Vigenere, Porta, Beaufort or Gronsfeld cipher a periodic I.C. calculation will identify large peaks at the length of the keyword. No other ciphers have this property.

If the cipher is polygraphic, the length must be a multiple of the graph size. E.g. If the ciphertext has an odd number of characters it can't be a bigraphic cipher (replaces pairs of characters) such as playfair or foursquare. If the length is not a multiple of 3 it can't be a 3x3 Hill cipher and so forth.

More Complicated Ciphers 
This page has a list of ciphers and their characteristics. If you have a large chunk of ciphertext the tables presented there can be used to narrow down the possibilities. The statistics in the tables can be computed with this calculator.

If all the above tests have failed, the cipher is probably a more complicated variant. From here it is usually easiest to make an educated guess on the cipher type, and try to break it under that assumption. If you don't break it, try another cipher type. Most ciphers in e.g. cipher challenges are made to be broken so they can't be too complicated.

----
(taken from practical cryptography)
