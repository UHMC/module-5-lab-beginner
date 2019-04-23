# Module 5 - Beginner Lab: Cryptography

## Background
Cryptography is the backbone of essentially all online financial systems; however, as you may have inferred from the term, cryptocurrencies are unequivocally dependent upon cryptography to function. In this lab, we will go through a basic cryptography exercise which introduces one of the better-known cryptographic tools available to the public: GPG, or Gnu Privacy Guard. As an aside, you may find the history of GPG quite interesting, as due to legal issues, it came to be offered as source code printed in a physical book which programmers could then write for themselves and compile into a working copy.

## Meta Information
| Attribute | Explanation |
| - | - |
| Summary | An introduction to cryptography using GNU Privacy Guard. |
| Topics | Cryptography, encryption, authentication. |
| Audience | CS1 or later. |
| Difficulty | Beginner. |
| Strengths | Introduces one of the better-known cryptographic tools and demonstrates its use. |
| Weaknesses | Greater focus on encryption than authentication. |
| Dependencies | Internet connected computer with installation rights or one with GPG previously installed with an already-published public key. |
| Variants | There is an intermediate counterpart to this lab which focuses on eliptic curve cryptography. |

## Assignment Instructions
1. Install [GNU Privacy Guard][gpg-site].
    * It is perhaps easiest to install gpg in Linux, but there are versions for Windows and Mac linked from the Download section of [the official site][gpg-site].
2. Run the following command in a terminal or command prompt and provide the appropriate details to the program:
    * gpg --full-gen-key
    * 1    // RSA & RSA
    * 4096 // Longest (most secure) supported at time
    * 2y   // Key expires 2 years from the date of creation
    * Your Name
    * youremail@emailprovider.net
    * aP455w0rdUW0n14G31
3. Run the following commands in a terminal or command prompt:
    * gpg --list-keys
    * gpg --output yourname.gpg --export youremail@emailprovider.net
        * Optionally, you can make the output in the form of text so you can publish it somewhere:
            * gpg --output yourname.gpg --export --armor youremail@emailprovider.net
4. To print to standard output, we can do:
    * gpg --armor --export youremail@emailprovider.net
5. Share the public key on a public key server like [pgp.mit.edu][pgp-mit].
6. Import someone else's public key to enable encrypting a message to them.
    * gpg --import theirname.gpg
    * gpg --list-keys   // should now show the new key added to your local keyring
    * gpg --fingerprint // does same thing but easier to read fingerprint format
    * gpg --edit-key theirname
    * help              // lists commands and what they do
    * fpr               // shows the fingerprint of the key being edited
    * Verify fingerprint of public key with owner, then sign it.
            * sign
    * check // displays signatures on key
    * save  // should exit; if not, run the command quit
7. Create a message to send to them.
8. Encrypt the message.
9. Give them the encrypted message.
10. After receiving an encrypted message, decrypt it.

## Credits
Dr. Debasis Bhattacharya  
Mario Canul  
Saxon Knight  

[gpg-site]: https://www.gnupg.org/
[gpg-manual]: https://www.gnupg.org/gph/en/manual/c14.html
[pgp-mit]: https://pgp.mit.edu/
