# guide to connect two PC's using ssh
* we will consider two PC's 
  * pc1
  * pc2
* here pc1 will be accessing pc2
* so, install openSSH Client on pc1 and openSSH Server on pc2
  * openSSH Client should be installed on the pc who will access other pc
  * openSSH Server should be installe don the pc which will be accessed by other pc
* now, generate a public/private keys using:
  ```shell
  ssh-keygen -t ed25519 -C '[email address]'
  ```
  * by using this 2 files will be created. one with .pub extension and other with no extension
    * .pub represents public key
    * file with no extension represents private key
* copy the .pub to ~/.ssh/ on pc2
* now, try to login into pc2 from pc1 by using
```shell
ssh [user username of pc2]@[ip address of pc2]
```
* example
```shell
ssh pio@192.168.48.01
```
