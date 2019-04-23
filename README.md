# Module 5 - Beginner Lab: Cryptography

## Background
Cryptography is the backbone of essentially all online financial systems; however, as you may have inferred from the term, cryptocurrencies are unequivocally dependent upon cryptography to function. In this lab, we will go through a basic cryptography exercise which introduces one of the better-known cryptographic tools available to the public: GPG (Gnu Privacy Guard). As an aside, you may find the history of GPG quite interesting, as due to legal issues, it came to be offered as source code printed in a physical book which programmers could then write for themselves and compile into a working copy.

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
    * It is perhaps easiest to install GPG in Linux, but there are versions for Windows and Mac linked from the Download section of [the official site][gpg-site].
2. Run the following command in a terminal or command prompt and provide the appropriate details to the program:
    * gpg --full-gen-key
    * 1    // RSA & RSA
    * 4096 // Longest (most secure) supported at time
    * 2y   // Key expires 2 years from the date of creation
    * Your Name
    * youremail@emailprovider.net
    * your comment
    * aP455w0rdUW0n14G31
3. To see your key, run the following commands in a terminal or command prompt:
    * gpg --list-keys
    * gpg --armor --export youremail@emailprovider.net
4. To export your key for publishing, either copy (all of) the output from the previous command, or run the following command and then copy all contents of the output file `yourname.gpg`:
    * gpg --output yourname.gpg --export --armor youremail@emailprovider.net
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
    * Use the text editor of your choice to create a message in a file in your working directory, naming it something like `message_for_bob.txt`.
8. Encrypt the message.
    * gpg --output message_for_bob.gpg --encrypt --recipient theiremail@emailprovider.net message_for_bob.txt
9. Give them the encrypted message.
    * I.e. share the file message_for_bob.gpg that was created.
10. After receiving an encrypted message, decrypt it.
    * gpg --output message_for_me.txt --decrypt message_for_me.gpg
    * Provide the password you created earlier.
11. You can now view the file message_for_me.txt with the the text editor of your choice.

## Credits
Dr. Debasis Bhattacharya  
Mario Canul  
Saxon Knight  

[gpg-site]: https://www.gnupg.org/
[gpg-manual]: https://www.gnupg.org/gph/en/manual/c14.html
[pgp-mit]: https://pgp.mit.edu/
