# Pretty Good Privacy (PGP) and GNU Privacy Guard (GPG) help

Contents:

* [Introduction](#introduction)
  * [What is Pretty Good Privacy?](#what-is-pretty-good-privacy)
  * [What is GNU Privacy Guard?](#what-is-gnu-privacy-guard)
  * [What is a digital signature?](#what-is-a-digital-signature)
* [Setup for your computer](#setup-for-your-computer)
  * [There are many ways to do this](#there-are-many-ways-to-do-this)
  * [Setup for macOS users](#setup-for-macos-users)
  * [Setup for Windows users](#setup-for-windows-users)
  * [Setup for Linux users](#setup-for-linux-users)
* [Create your PGP key](#create-your-pgp-key)
* [Verify your new key is included in GPG](#verify-your-new-key-is-included-in-gpg)
  * [Verify your new key by using its id](#verify-your-new-key-by-using-its-id)
* [Export your PGP key files](#export-your-pgp-key-files)
* [Encrypt](#encrypt)
* [Decrypt](#decrypt)
* [Decrypt with base64](#decrypt-with-base64)
  * [For macOS](#for-macos)
  * [Decrypt the file](#decrypt-the-file)


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

* [https://github.com/joelparkerhenderson/pgp_gpg_help](https://chrome.google.com/webstore/detail/pgp-anywhere/cdlcdnmhcodhagbmljapgbjdimjckilb): Use PGP wherever you are, including encryption and digital signatures. Features full clientside encryption of your keyring, cloud synchronization, anonymous use, and more. Simple, fast, and open source.


### Setup for macOS users

Ensure your macOS is fully up to date:

* Choose the Apple menu, then "About this Mac", then click the button "Software Update".

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

Ensure Xcode is installed, and brew is up to date and working correctly:

```
xcode-select --install
brew update
brew upgrade
brew cleanup
brew doctor
```

Install GPG with brew by typing:

```
brew install pkg-config
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

If you want to cancel the program at any time, press control-c.

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

The program prompts:

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


## Encrypt

Suppose you want to encrypt a message.

Create a typical text file with a file name such as `message.txt`

Put some text in it such as:

```
hello world
```

Encrypt with your own public key:

```
gpg --encrypt --recipient alice@example.com --output message.gpg message.txt
```

GPG creates a new encrypted file with the file name `message.gpg` 

The encrypted file is now fully protected, and only you are able to decrypt it, because only you have the private key.

If you want to encrypt a message for someone else, then you obtain their public key, add it to your GPG, and then you can encrypt a message with their public key. Learn about this in the [GPG manual](https://www.gnupg.org/documentation/manuals/gnupg/)


## Decrypt

Suppose you want to decrypt a message, such as the file `message.gpg` from the section above.

```
gpg --decrypt message.gpg
```

The output should show information about the encryption, the key, and the message text, such as:

```
gpg: encrypted with 4096-bit RSA key, ID 20207FFA970D5D16, created 2020-03-23
      "Alice Adams <alice@example.com>"
hello world
```

If you want to decrypt a stream, you can pipe input into GPG such as:

```
cat message.gpg | gpg --decrypt
```


## Decrypt with base64


Suppose you want to decrypt a message, such as this message text that is also encdoded using base64:

```
wcFMAyAgf/qXDV0WARAALV0cccfFRBwUBpnj4f8wf7V+GJXHlfDJHfFuVx+V7GZr3PQqKkTH5l
Wyjq1kWwpnNXoUn4Fcn+N9WM2XgHPeN0+t5wsNezrzmlNbhHfmFW5kB1RKJQB3rGWnnyj4HSDV
sCIFJz+yxna/UKh7wM0wrvTcIns+ItLioWkA/Oq7bcS9cINm8HcSFZ6VY2p4rLg6qbk+wjkQ2c
PAss2h52hMzITKbRxvThJfqiT8xIPjZacHSTeGbfnzof5VWyi5sBdriZri4xmZPBRyzgesyVZM
IqBIzx85GkMTPp8OXJh7N51sQiPd3E9xoW5ZmTXGDGfgatmMWpE27QFKUnNWSJ/braqaHZCsWk
/ZOeEJjgrFEvjZD7ajyTTRAi1Y40BscYTLuGoJ6xb9GDxyoJ809jXgynQTkQ+XaRVphCkAYPON
ikniukjUd3x4qQp2gHGLtzLrmbm9Dvx0Mk/nRwnTc52+llft+WF/2TMivD/y2wb5qIp0m8pM0p
YrXoAMh1wOHUwVFrkVz/WsQIH3AfTpPl4iyPdQzL5t6kdKq7QMuQNlKzK8oBHFVTYFdNiQ5//l
zZ0DrB2NT+DXS5sdw3z8BHpYWyOwvXb34F98B3aid+nwifBU5b9rERn2Y0Y9U19xUVXgWNg2uo
1aqD5gFWhgTaK6dQSbTKbtKTb/pH+8mfVDDrS4AHkHEMst740umPEq8SMU/PLSOGQw+DL4PDh2
HXgYuL3nYbz4F7lI8jd/3T5HC61x+g55LuOWeV57mhm/K0lDRm/KkOEtX/gROSB/CfNBou8DHz
iIPNq2O1w4gskB1rh21oA
```

Save the message text in a new file, such as file name `message.gpg`.

* The message text must be all one line, with no spaces, no newlines, no returns.

* The slash character is a normal character, not a line wrapping character.

When you save the message text, be careful about your text editor:

* Some text editors automatically insert extra line wrapping characters, or an extra final newline character; delete these extras.

* Some text editors show visual line wrapping, even without the presence of line wrapping characters; ignore this visual line wrapping.

Examples for specific text edtiors:

* For text editor "vi" or "vim": the message text typically goes all the way across your screen multiple times; at the bottom, the status line indicates the text has no end-of-line and is 1 line long such as: `"~/message.gpg" [noeol] 1L, 836C`.

* For text editor "emacs": the message text typically goes all the way across your screen multiple times; at the bottom, the status line indicates the text has 1 line long such as: `message.gpg All (1,0)`.

* For text editor "Sublime": you may want to turn on visual line numbering; the text area left column indicates that your text  is 1 line.


### For macOS

You might need extra steps to decrypt the password:

``` 
brew install pinentry-mac

echo "pinentry-program /usr/local/bin/pinentry-mac" \
>> ~/.gnupg/gpg-agent.conf

gpgconf --kill gpg-agent

killall gpg-agent

gpg-agent
```


### Decrypt the file

Decrypt the password:

```
cat message.gpg | base64 --decode | GPG_TTY=$(tty) gpg --decrypt
```

If you get this error...

```
gpg: encrypted with 4096-bit RSA key, ID 10972DD260CD2D6B, created 2020-01-01
      "Alice Adams <alice@example.com>"
gpg: public key decryption failed: No such file or directory
gpg: decryption failed: No secret key
```

...then verify that you do hav your corresponding secret key:

```
gpg --list-secret-keys
```

If you stil get the error, then try restarting the program `gpg-agent` such as:

```
gpgconf --kill gpg-agent
killall gpg-agent
gpg-agent
```

...then you should see:

```
gpg-agent[…]: gpg-agent running and available
```

If you get this error...

```
gpg-agent[…]: no gpg-agent running in this session
```

..then verify that your versions of `gpg-agent` and `gpg` are identical and 2.2 or higher - this isn't strictly necessary yet it's good practice and can help protect you from incompatibility bugs:

```
gpg-agent --version 
gpg --version
```

...then try replacing the program `gpg` with `gpg2` like this:

```
cat message.gpg | base64 --decode | GPG_TTY=$(tty) gpg2 --decrypt
```

If you get this error...

```
command not found: gpg2
```

...then verify you have GPG 2.x:

```
brew info gpg 
```

...and you should see something like:

```
gnupg: stable 2.2.20 (bottled)
GNU Pretty Good Privacy (PGP) package
```

If you try this...

```
brew install pkg-config
```

...and get this kind of error message...

```
pkg-config is outdated
```

...then you need to update your system softwrare, such as by using the instructions near the top of this document.

If you're still having issues, see https://serverfault.com/questions/481103/gpg-agent-says-agent-exists-but-gpg-says-agent-doesnt-exist
