# UPitts_InformationSecurityAndPrivacy    
First Semester, Information Security and Privacy    
IS-2150/TEL2810: Information Security and Privacy, Fall 2017    
Programming Project     
1. Message Digest [15 Points]    
Write a program to demonstrate the use of hashing using MD5 and SHA scheme and the
MessageDigest class.
Your program should allow a user to enter a string; the program then hashes it and outputs the result.
You will need to consult Java API documentation to learn how to use java classes. You can
download and install the documentation yourself, or you can access them from this URL:
http://java.sun.com/j2se/1.4.2/docs/api/index.html
2. Crypto Techniques    
The objective of this exercise is to use Java features to write some security mechanisms that can
be used in applications. You will be using the classes from Java Cryptographic Extension to
implement them.
You will need to consult Java API documentation. You can download and install the documentation
yourself, or you can access them from this URL:
http://java.sun.com/j2se/1.4.2/docs/api/index.html
Java books that you can reference
Inside Java 2 Platform Security, 2nd Edition, L. Gong, G. Ellision, M. Dageforde
Java Security, Scott Oaks, O’Reilly
For each part of the assignment, skeleton Java code has been provided. These skeletons will NOT
compile. You will need to make modifications on them before they can be successfully compiled and
run.    
2.1) Signature [15 points]    
In this part of the assignment, you are to implement the ElGamal Signature scheme described in the
textbook in section 10.6.2.2.
There are two classes in this assignment, ElGamalAlice and ElGamalBob, corresponding to the
sender (Alice) and the receiver (Bob). The main functions for both the classes have been written for
you. Your assignment is to write various functions that implement ElGamal key generation and
signature creation algorithms (for Alice), and signature verification algorithm (for Bob). The
functions you have to implement are indicated in the source files.    
2.2 Encryption [20 points]    
In this part of the assignment, the client program CipherClient should (1) generate a DES key
and stores the key in a file, (2) encrypts the given String object using that key and sends the
encrypted object over the socket to the server. The server program CipherServer then uses
the key that was previously generated by the client to decrypt the incoming object. The server
obtains the key simply by reading it from the same file that the client previously generated.
The server should then print out the decrypted message. For this part of the assignment, you
will need to consult external sources and documentations on how to generate a DES key,
write to or read from a file, and perform encryption/decryption of an object.
Most of the needed information should be available at:
http://java.sun.com/products/jce/doc/guide/API_users_guide.html    
3. Breaking a Substitution Cipher    
The objective of this component of the project is to demonstrate the vulnerabilities of simple
substitution ciphers. You will implement a simple mono-alphabetic substitution namely a shift
cipher and break its key using alphabet frequency correlation.
Description:    
3.1 [15 points]    
In the first part of this assignment, you need to implement the encryption and decryption
algorithms for a shift cipher. Your encryption program should take the encryption key and the
plain text (an input file) as inputs and should produce the cipher text as an output file. Similarly,
your decryption program takes the key and the cipher text file as an input and produces the plain
text back.    
3.2 [35 points]    
For the second part of this lab assignment, you will implement a cryptanalysis tool to break the
shift cipher that you implemented in the first part. Concretely, your program should a ciphertext
as input, find the frequency of distribution of the letters in the cipher-text and compute its
correlation with the English alphabets for various possible values of the encryption keys. Your
program should display the encryption keys and plain texts corresponding to top 7 correlations
with their correlation values. Table 1 shows the frequency distribution of the English alphabets
and you need to use these exact values for the frequency distribution of plain text characters.
An illustrative example is shown below to explain the various steps involved in the cryptanalysis
process.    
Consider a plaintext P :HELLO WORLD and C (ciphertext): khoor zruog
It is obtained as a result of a shift cipher with key k = 3
ci=E(pi)=pi+3 mod 26
The goal of the cryptanalysis process is to guess the encryption key , k (which is 3 in this
example) through correlating the frequency distribution of the cipher text letters with that of the
plain text.
Table 1: Frequency of English alphabets
§
§
§
§
We already have the plain text letter frequency distribution is Table 1. Therefore, we now
compute the frequency of the letters in the ciphertext, ‘khoor zruog’
Let f(c) denote the frequency of letter c in ciphertext
§ In the given cipher text ‘khoor zruog’, we have 10 characters in total
§ 10 characters: 3 * ‘o’, 2 * ‘r’, 1 * {k, h, z, u, g}
§ Therefore the values of f(c) is shown below for various letters in the ciphertext:
f(g)=0.1 f(h)=0.1 f(k)=0.1 f(o)=0.3 f(r)= 0.2
f(u)=0.1 f(z)=0.1 f(ci) = 0 for any other ci
§ We have 26 possible keys for a shift cipher. For each key i, we need to compute the
correlation of frequency of cipher text letters to that of the plaintext.
§ For key i, let ϕ(i) denote the correlation of frequency of letters in ciphertext with
frequency of corresponding letters in English
a 0.080 h 0.060 n 0.070 t 0.090
b 0.015 i 0.065 o 0.080 u 0.030
c 0.030 j 0.005 p 0.020 v 0.010
d 0.040 k 0.005 q 0.002 w 0.015
e 0.130 l 0.035 r 0.065 x 0.005
f 0.020 m 0.030 s 0.060 y 0.020
g 0.015 z 0.002
§ For each key i: ϕ(i) = Σ0 ≤ c ≤ 25 f(c) * p(c – i)
§ Here c is a representation of character (a-0, ..., z-25)
§ f(c) is frequency of letter c in ciphertext C
§ p(x) is frequency of character x in English
§ For our example: C = ‘khoor zruog’ (P = ‘HELLO WORLD’)
f(c): f(g)=0.1, f(h)=0.1, f(k)=0.1, f(o)=0.3, f(r)=0.2, f(u)=0.1, f(z)=0.1
c: g = 6, h = 7, k = 10, o = 14, r = 17, u = 20,
z = 25
Therefore, ϕ(i) = 0.1p(6 – i) + 0.1p(7 – i) + 0.1p(10 – i) +
+ 0.3p(14 – i) + 0.2p(17 – i) + 0.1p(20 – i) +
+ 0.1p(25 – i)
Table 2 : Frequency correlation between plain text letters and cipher text letters.
We can obtain the values of ϕ(i) for each value of i using the frequency values shown in Table 1.
The values of ϕ(i) is shown in Table 2.
i ϕ(i) i ϕ(i) i ϕ(i) i ϕ(i)
0 0.0482 7 0.0442 13 0.0520 19 0.0315
1 0.0364 8 0.0202 14 0.0535 20 0.0302
2 0.0410 9 0.0267 15 0.0226 21 0.0517
3 0.0575 10 0.0635 16 0.0322 22 0.0380
4 0.0252 11 0.0262 17 0.0392 23 0.0370
5 0.0190 12 0.0325 18 0.0299 24 0.0316
6 0.0660 25 0.0430
In the next step, we consider the values of i corresponding to the top 4 correlation values in
Table 2. (We consider top 4 in this example, however, in your program you need to consider top
7 correlation values).
♦ Top 4 probable keys (largest ϕ(i) values) and the corresponding plaintexts:
– i = 6, ϕ(i) = 0.0660
• plaintext EBIIL TLOLA
– i = 10, ϕ(i) = 0.0635
• plaintext AXEEH PHKEW
– i = 3, ϕ(i) = 0.0575
• plaintext HELLO WORLD
– i = 14, ϕ(i) = 0.0535
• plaintext WTAAD LDGAS
We know that we find an English phrase for only i = 3. Therefore, the key is (3 or ‘D’) and
thus broken.
Your program needs to show the top 7 correlation values and their corresponding keys and plain
texts. It thereby serves as a tool to an attacker by presenting the most probable plain texts for a
given cipher text.
Deliverables.
(1) A short report (3 pages or so). The report should contain one example for each
component of the project where you will present the input data and the output produced
by your program.
(2) A tarball (.tar.gz file) or a zip file (.zip file) containing all the programs required to run
your code.
(3) Team member evaluation if there is any issue that needs attention of the instructor.
Each team only needs to submit one deliverable package to courseweb before the deadline. In
addition, you will be required to present a short demo to the instructor. You can email and talk to
the instructor and GSA for any questions and clarifications and seek possible help and advice
that you may need during the course of this project.
