# PEKS

This is the implementation of public-key searchable encryption using bilinear maps described in 
Public Key Encryption with Keyword Search. It is a simple, command-line application developed in C.

## Implementation Details

#### Dependencies

* GMP Library: 

  ```$ sudo apt-get install libgmp3-dev```
* OpenSSL: 

  ```$ sudo apt-get install libssl-dev```
* [PBC Library](https://crypto.stanford.edu/pbc)
http://crypto.stanford.edu/pbc/download.html
![image](https://user-images.githubusercontent.com/40285558/193268795-831ebc8a-05d9-4b1f-89d3-16a76df14fc5.png)
 ```

  sudo apt install m4 %注意小写m，装不上，先sudo apt update一下
  sudo apt install flex
  sudo apt install bison %几个依赖包
  ```

  ```
  $ ./configure --prefix=$HOME/.local
  $ make
  $ make install
  ```
  if ./configure --prefix=$HOME/.local is not work, we can modefiy C file head, such as 
    ```
  #include "/usr/local/include/pbc/pbc.h"
    ```
    in Default Installation path  /usr/local/lib
  Makefile uses this path. In case of change in destination directory, update the Makefile accordingly.
  
  ![Uploading image.png…]()
  Display on PBC installation ready

#### Build

   ```$ make```
   if make is not work, second way is “gcc main.c peks.c -o peks -lpbc -lssl -lcrypto -lgmp -lm”

#### Run

   ```$ ./peks <word1> <word2>```

#### Usage

```
$ ./peks hello hello
Equal
$ ./peks Hello hello
Not equal
$ ./peks Supercalifragilisticexpialidocious Supercalifragilisticexpialidocious
Equal
$ ./peks Lopadotemachoselachogaleokranioleipsanodrimhypotrimmatosilphioparaomelitokatakechymenokichlepikossyphophattoperisteralektryonoptekephalliokigklopeleiolagoiosiraiobaphetraganopterygon Lopadotemachoselachogaleokranioleipsanodrimhypotrimmatosilphioparaomelitokatakechymenokichlepikossyphophattoperisteralektryonoptekephalliokigklopeleiolagoiosiraiobaphetraganopterygon
Equal
$ ./peks Lopadotemachoselachogaleokranioleipsanodrimhypotrimmatosilphioparaomelitokatakechymenokichlepikossyphophattoperisteralektryonoptekephalliokigklopeleiolagoiosiraiobaphetraganopterygon Lopadotemachoselachogaleokranioleipsanodrimhypotrimmatosilphioparaomelitokatakechymenokichlepikossyphophattoperisteraletryonoptekephalliokigklopeleiolagoiosiraiobaphetraganopterygon
Not equal
```

*This work was a part of the master thesis from TU Dresden under the supervision of Dr. Josef Spillner and Martin Beck.

## [Public Key Encryption with Keyword Search](http://eprint.iacr.org/2003/195.pdf) 

by Dan Boneh, Giovanni Di Crescenzo, Rafail Ostrovsky and Giuseppe Persiano.

The authors describe a way of appending information to a message that has 
been encrypted with a standard  public key cipher, which allows a server 
that doesn’t have the private key necessary to  decrypt the entire message
to still be able to search for a certain set of keywords. For a keyword, a 
PEKS value can be generated which will allow the server to perform a search
using a trapdoor.

This was modified in 2022.9.30 by Ben
