### Cryptography
	: the art and science of keeping infromation secure through the use of mathematical concepts and techniques.
How does Cryptography fit into our CIA triad and the core of defending systems.
	Confidentiality is focused on keeping information and communication secure from unauthorized parties.
		_A primary method for keeping information secure is cryptography._
Cipher
	: a method of designing secret or hidden messages.
plaintext vs ciphertext
	: how we refer to text that is not encrypted vs. encrypted.
Ceasers cipher
	was an encryption method made by ceasar in order to encrypt messages with a rotation style encryption
		_with rot13 characters are rotated 13 positions_
Enigma machine
	an encryption made by the nazis in world war 2 which encrypts by the user moving wires to make characters scrambled and the key for decryption would be saved each day
		_rotating decryption keys is a prominent part of cyber security professionals duties today._
![[Pasted image 20220927185219.png]]
Encoding
	: used to transform data so it can be properly used by different types of systems. It is not used to keep infromation secret, and data is encoded with publicly available schemes that can be decoded by anyone.
		**Binary** - contains only zeros and 1's
		**Decimal** - convert binary to decimal to then convert to ascii but decimal contains numbers 0-9
		**ASCII** - letters (uppercase and lowercase) and numbers as well as special characters _look at your keyboard._
		**Hex** - uses 16 symbols total which are 0-9 and A-F
		**Octal** - looks similar to hex but only uses digits 0-7
Encryption
	: Used to keep information from being accessed by unauthorized parties. Encyption occurs on binary data and any other data is converted to binary in order to encrypt it.
The P.A.I.N model
	Privacy, Authentication, Integrity, Non-repudiation
		Non-repudiation : encrypting something so that you can tell it is not replicable meaning you can tell who did the action
Algorithms
	: mathematical instructions that ciphers use for encryption.
Stream Ciphers
	: apply their algorithm one character at a time.
		**Substitution cipher** - substitutes out old values for new values.
Block ciphers
	: breaks an input message in to equal-sized blocks and rearrange the letters of each block.
Key space
	: a possible range of nujbers that can be used as a key
		For modern cryptography, key space is defined by the number of binary bits used in the key known as **bit size**
Modern symmetric key algorithms
	: use algorithms that are secure and fast.
		_symmetric key algorithms use a single, shared key to encrypt and decrypt a message. This shared key needs to remain private. If exposed, the message can be decrypted by anyone._
	DES - dead
	3DES - dead
	AES - current standard
```bash
#Create message
echo "this is a secret message" > plainmessage.txt

#Create Key and IV
openssl enc -pbkdf2 -nosalt -aes-256-cbc -k mypassword -P > key_and_IV
cat Key_and_IV

#Encrypt message
openssl enc -pbkdf2 -nosalt -aes-256-cbc -in plainmessage.txt -out plainmessage.txt.enc -base64 -K <key> -iv <IV>

cat plainmessage.txt.enc

#Decrypt message option -d
openssl enc -pbkdf2 -nosalt -aes-256-cbc -in plainmessage.txt.enc -d -K <KEY> -iv <IV>
```
openssl
	: a free command-line tool used for symmetric encryption and decryption.

#### Symmetric Encryption
Disadvantages
	Exchanging keys for decryption
		**Offline exchange** - Physically reading the key over the phone or mailing so the key cant be picked up from internet communications.
		**DIffie-Hellman Key Exchange** - complex mathematical principles to create a shared secret key between two parties over a public channel.
	Key management
		Each person needing to communicate would need a key exchange with every person they communicate with (n*(n-1))/2
#### Asymmetric Encryption
How it works
	**Private keys** are kept secret and can afffect confidentiality of messages if exposed, whereas **Public keys** are public and accessible to all.
		Person A sends an encrypted message that was encypted using Person B's public key which can only be decrypted by Person B's private key which only the carry.
RSA
	: is the asymmetric algorithm standard used around the world. It works by employing the complexity of factoring large numbers.
#### GPG
	: used to simplify the creation, encryption, and decryption of asymmetric key cryptography.
DEMO // CREATING KEYS
```bash
# Create Key Pair
gpg --gen-key
	# Enter name:
	# Enter email:
	# O for Okay
	# Enter Password:

# View Keyring
gpg --list-keys

# Export public key (remember available to everyone)
gpg --armor --output name.gpg --export email@email.com
cat name.gpg
```
UTILIZING
```bash
# Check key chain (empty)
gpg --list-keys

# Import Public Key (user1)
gpg --import user1.gpg
gpg --list-keys

# Create Plaintext message
echo "keep this secret: MyPassword123" > password.txt

# Encrypt message using user 1 public key
gpg --armor --output password.txt.enc --encrypt --recipient
email@email.com password.txt

cat password.txt.enc
```
DECRYPT
```bash
gpg --decrypt password.txt.enc
```
Hashing
	: a cryptographic method used to verify the integrity of data.
		_hashing is a one way street while encryption is a two way. hashes do not have keys._
DEMO // HASHES
```bash
# Create file
echo "This is my first hashing activity" > secretmessage.txt

# Create md5 hash
md5sum secretmessage.txt > hashes.txt
cat hashes.txt
md5sum secretmessage.txt
	# observe same hash, repeatable

# Modify secretmessage
echo "This is my First hashing activity" > sercretmessage.txt

# Check md5sum
md5sum secretmessage.txt
	# observe very different
md5sum -c hashes.txt
	# observe fails
```
_Encryption's main goal is privacy. Hashing's main goal is integrity._
#### Digital Signatures
	: a mathematical scheme used to verify the authenticity of  digital data.
How its done?
	Key Creation
		Person A creates a private and public key
	Creating the Message
		Person A stores their message in a file
	Signing the message
		Person A signs the message with their private key in order to create a digital signature.
	Sending the message
		Person A sends the digital signature to Julie along with his plaintext message.
	Validating the signature
		Person B uses Person  A's punlic key to validate the signature with GPG
DEMO // DIGITAL SIGNATURES
```bash
# See Demo on creating gpg keys above
--------------------------------------
# Sign message
gpg --output name_signature --armor --detach-sig message.txt
	# enter password
cat name_signature

sudo chmod 777 message.txt # Only needed if replicating on same machine ex: sysamdin and instructor in bootcamp VM

# send message and signature to user1
```
IMPORTING AND VERIFYING SIGNATURES
```bash
# See Demo on importing user above
-------------------------------------
gpg --verify name_signature message.txt
	# observe GOOD signature

vi message.txt
	# modify
gpg --verify name_signature message.txt
	# observe BAD signature
```

### Applied Crypto and Attacks
Secure Socket Layer (SSL)
	protocol designed to encrypt web traffic.
		_HTTPS acutally stands for HTTP over SSL_
	Websites use SSL certificates as seals of approval to confirm a website can be trusted.
		These certificates use public key cryptography to establish a secure connection between the browser and server.
Forensic Examiner
	cybersecurity professional who captures and investigates digital evidence from computers, cell phones, and other devices containing digital data.
Steganography
	the cryptographic technique of placing hidden messages within files, images, or videos
STEGHIDE DEMO
```bash
#observe family.jpg

# Create message
echo "this is a hidden message" > hidden_message.txt

#Hide message
steghide --help
	# -cf = coverfile
	# -ef = embedfile
	# -sf = stego file
steghide embed -cf family.jpg -ef hidden_message.txt
	# enter password
rm hidden_message.txt

#Extract message
steghide extract -sf family.jpg
	# enter password
ls
cat hidden_message
```
SSL ceritficates
	: small data files that use public key cryptography to secure connections between the browser and the web server.
		_to acheive this cerificate an organization must first reach out to a **certificate authority** (CA), an organization responsible for issuing SSL cerificates._
			X.509 is the current standard of SSL cerrificates for securing online communications
Statistical Attack
	: exploits weakness in cryptographic algorithms by attempting to determine if the "random" values produced are actually predictable.
Frequency Analysis
	: a method for cracking substitution algorithms
Replay Attacks
 	: attacker intercepts an encrypted message and replays it to the receiving party to get access.
Rainbow Tables
	: resources that contain precomputed hashes with the associated plaintext passwords.
Salting
	We can defend against rainbow tables by salting, a cryptographic method of combining salt (a random value) with the plaintext into the hash function
HASHCAT DEMO
```bash
#Crack hash
hashcat -m 0 -a 0 -o solved.txt hash.txt
/usr/share/wordlists.rockyou.txt --force
```
