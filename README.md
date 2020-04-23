# Pretty Good Privacy (PGP) and GNU Privacy Guard (GPG) help

Contents:

* [](#)


## Introduction


### What is Pretty Good Privacy?

https://en.wikipedia.org/wiki/Pretty_Good_Privacy

Pretty Good Privacy (PGP) is an encryption program that provides cryptographic privacy and authentication for data communication. PGP is used for signing, encrypting, and decrypting texts, e-mails, files, directories, and more.


### What is GNU Privacy Guard?

https://en.wikipedia.org/wiki/GNU_Privacy_Guard

GNU Privacy Guard (GPG) is free open source encryption software. GPG can use both conventional symmetric-key cryptography for speed, and public-key cryptography for secure key exchange. GPG encrypts messages using asymmetric key pairs that are individually generated by GPG users. GPG implements encryption that is compatible with the OpenPGP standard.


### What is a digital signature?

https://en.wikipedia.org/wiki/Digital_signature

A digital signature is a mathematical scheme for verifying the authenticity of digital messages or documents. A valid digital signature, where the prerequisites are satisfied, gives a recipient very strong reason to believe that the message was created by a known sender (authentication), and that the message was not altered in transit (integrity).


## Setup for your computer


### There are many ways to do this

PGP and GPG have many approaches and programs to help create encryption and manage your security credentials.

Examples of applications:

* [GPG Tools](https://gpgtools.org/): a whole package of GPG based software tools. This suite contains four tools to bring encryption in all areas of your Mac system. Every software is based on GnuPG. The package contains an email plugin for Apple Mail, a key manager, a Service to use GPG in almost any application and an engine to use GPG with the command line.

* [Gpg4win](https://www.gpg4win.org/): enables users to securely transport emails and files with the help of encryption and digital signatures. Encryption protects the contents against an unwanted party reading it. Digital signatures make sure that it was not modified and comes from a specific sender. Gpg4win supports both relevant cryptography standards, OpenPGP and S/MIME (X.509), and is the official GnuPG distribution for Windows. It is maintained by the developers of GnuPG. 

Examples of browser extensions:

* [Mailvelope](https://addons.mozilla.org/en-US/firefox/addon/mailvelope/): adds encryption and decryption features to the user interface of common webmail providers, including Gmail, Outlook, and more. It supports the PGP encryption standard (OpenPGP, GPG) and is compatible with other PGP applications. Encrypt files on your hard drive with Mailvelope and send encrypted email attachments.

* [https://chrome.google.com/webstore/detail/pgp-anywhere/cdlcdnmhcodhagbmljapgbjdimjckilb): Use PGP wherever you are, including encryption and digital signatures. Features full clientside encryption of your keyring, cloud synchronization, anonymous use, and more. Simple, fast, and open source.


### Setup for macOS users

Open the app “Terminal”.

Check if you have the terminal tool “Homebrew” available by entering this:

```
brew --version
```

The output should look something like this:

```
Homebrew ...
```

If the output looks something like this...

```
command not found: brew
```

...then go to https://brew.sh/ and follow the instructions to install Homebrew.

Install GPG with brew by typing:

```
brew install gpg
```

### Setup for Windows users

Download and install [Gpg4win](https://www.gpg4win.org/)


### Setup for Linux users

Use your system package manager to install GPG.

For Ubuntu and Debian:

```
sudo apt-get install gpg
```

For Red Hat and CentOS:

```
sudo yum install gpg
```

For BSD and FreeBSD:

```
sudo pkg_add gnupg
```


## Create your PGP key


Create your personal PGP key with our typical settings for OpenPGP:

```
gpg --full-gen-key --openpgp
```

The program requires you to complete the setup in a short amount of time. If you run out of time, that's fine.

If the program prompts:

```
gpg: agent_genkey failed: Timeout
Key generation failed: Timeout
```

Then just run it again:

```
gpg --full-gen-key --openpgp
```

The command prompts for choices, such as one or more of the items below.

```
Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
   (3) DSA (sign only)
```

Choose RSA and RSA. This is typically the default.


The program prompts:

```
RSA keys may be between 1024 and 4096 bits long.
```

Choose 4096 bits. 

* This is typically the strongest.

* This takes slightly-longer to compute.

The program prompts:

```
Please specify how long the key should be valid.
```

Choose 0. 

* This means “key does not expire”.

* Professionals typically choose a timerange, such as one year or less, because this ensures that keys expire.

The program might prompt:

```
Key does not expire at all
Is this correct? (y/N)
```

Enter "y".

The program prompts:

```
Real name: 
```

Enter your real name such as “Alice Adams”.

* You can use any kinds of characters, including capitals, spaces, etc.

* This is a real name field, not a username field.

* The information is to show other people who you are, and that this is your key.

* If you prefer to use something other than your real name, you can.

* Some people prefer to use a nickname, or handle, or URL.

Email address: enter your email address.

* Question: What happens if I lose access to the email? Answer: Generally you would want to revoke the key; the email address doesn't actually matter for the key itself, but it does matter if someone who uses your key needs to get in touch with you.

* Question: How do I revoke a key? Answer: See below. 

* Question: Can I have more than one key? Answer: Yes, and professionals tend to have many keys, such as one key per purpose, or project, or domain; this is more complex to manage.

* Question: Where is my name and/or email address sent/published/disclosed? Answer: To whomever you send your public key, and generally you should expect this information to be truly public.

* Question: Can I use an email address with a plus code? Answer: Yes, if your email provider supports this; for example, you can use an email adress such as "alice+pgp@example.com".

The program prompts:

```
Comment: 
```

You can leave it blank.

The program prompts:

```
Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit?
```

Enter "O" meaning Okay.

The program prompts:

```
Passphrase: 
```

Make up a long secret complex passphrase that you do not use elsewhere. 

* Ideally it should be at long, at least 20 characters, and random. 

* If you use a password generator, such as 1Password, LastPass, BitWarden, etc., then you can use it. 

* If you do not use a password generator, then you can try something like this https://www.textfixer.com/tools/random-string-generator.php TODO find a better password generator.

The program tests your passphrase, and might show this:

```
Warning: You have entered an insecure passphrase. 
A passphrase should contain at least 1 digit or special character.
<Take this one anyway> <Enter new passphrase>
```

Try a new passphrase that is longer, more complex, and has a digit and a special character such as punctuation.


TODO how do I cancel? ctrl-C

The program may say “We need to generate some random information....” Follow the instructions on your screen.

If the program prompts you for <OK> or <CANCEL> then choose OK. 

* To choose OK, make sure OK is selected then press return. 

* To change which one is selected, press tab.

The program should say something like “Trusted”, or “Key marked as trusted”, or “Created revocation certificate”, or “Public key created and signed”.

The program should output information about your new key.


## Verify your new key is included in GPG

To list all your keys:

```
gpg --list-keys
```

The output will look something like this:

```
gpg: checking ...
gpg: marginals ...
gpg: depth ...
gpg: next ...
.../.gnupg/pubring.kbx
-----------------------------------
pub   rsa4096 2020-04-16 [SC] [expires: 2021-04-16]
      E95D0925931A45FE00E1D1FC0245BD78EEBC27FB
 uid           [ultimate] Alice Adams <alice.adams@example.com>
 sub   rsa4096 2020-04-16 [E] [expires: 2021-04-16] 
```

The long line of letters and number is your key id, such as:

```
E95D0925931A45FE00E1D1FC0245BD78EEBC27FB
```

* Sidenote: the output says the word “ultimate” when it’s a key that you trust fully. This is always true for your own key.


### Verify your new key by using its id

List a key by using this syntax:

```
gpg --list-key <id>
```

In the syntax above, the angle brackets mean "replace this <id> with your own key id.

Note: the ID is public, so you can share it with people.


Example:

```
gpg --list-key E95D0925931A45FE00E1D1FC0245BD78EEBC27FB
```

Output should show your key information.


## Export your PGP key files

Export your public key, in a format using ASCII armor block, and save it to a file:

```
gpg --export --armor <id> > pgp-public-key-block.txt
```

Verify the file is created:

```
ls pgp-public-key-block.txt
```

Output should show the file name:

```
ls pgp-public-key-block.txt
```

If the output shows “No such file” then there’s a problem, and please ask for help.

If you want to know what directory you are currently in, then use the command "present working directory" like this:

```
pwd
```

Sidenote: the text looks something like this:

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
[massive block of garbled text]
-----END PGP PUBLIC KEY BLOCK-----
```

Sidenote: you can export the key to your screen:

```
gpg --export --armor <id>
```

Export your private key, in a format using ASCII armor block, and save it to a file:

```
gpg --export-secret-key --armor <id> > pgp-private-key-block.txt
```

Sidenote: the text looks something like this:

```
-----BEGIN PGP PRIVATE KEY BLOCK-----
[massive block of garbled text]
-----END PGP PRIVATE KEY BLOCK-----
```

Sidenote: you can export the key to your screen:

```
gpg --export-secret-key --armor <id>
```

Generate a way to revoke, in a format using ASCII armor block, and save it to file:

```
gpg --gen-revoke --armor <id> > pgp-revoke-block.txt
```

Sidenote: you can export the key to your screen:

```
gpg --export-secret-key --armor <id>
```

You can now share your file `pgp-public-key-block.txt` with anyone you want.

