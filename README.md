# Using OTP with Python

<br>
<br>
<br>

# Introduction
One-Time Password(OTP) is a password that is used for one login session on a user's device. OTPs can be delivered to users through text messages, authenticator apps, email, and more. It can be used as an additional layer of security for users to confirm their identities. The purpose of this lab is to learn about OTP and how it can be used in real world scenarios.

<br>
<br>
<br>

# Technologies Used

- Python
- Authenticator App (Microsoft Authenticator)



# Project
I first imported the required libraries for this project. The required libraries for this project were, pyotp, qrcode and getpass. 

```
import pyotp
import qrcode
import getpass
```

```
key = pyotp.random_base32()

print(key)
```

This code generated a random secret key which was used for the next code. It changes everytime you execute it.

![1](https://github.com/obi298/Using-OTP-with-Python/assets/90945162/a0149d3d-c436-4768-abb6-f7794f05ba55)


This is an image of me entering the secret key.

![2](https://github.com/obi298/Using-OTP-with-Python/assets/90945162/1d72f98f-72c4-4015-8f1a-1d87ff79aa48)

```
key = '4FFL2ENARCIW423Y6SK4JDSJVLT3Q4KI'

totp = pyotp.TOTP(key)
```

<br>

I then created the user's name and issuer name which was be displayed on the authenticator app. 


![3](https://github.com/obi298/Using-OTP-with-Python/assets/90945162/65507901-e213-4df2-b4a0-5a7469c4d689)

<br>

```
uri = pyotp.totp.TOTP(key).provisioning_uri(name= "user", issuer_name= "Company" )
print(uri)

qrcode.make(uri)
```

I was able to create a URI and generate a QR code which was scanned with my authenticator app. I decided to use Microsoft Authenticator for this project. 
As you can see from this image, the username, issuer name, and secret key are all displayed in the URI.


![4](https://github.com/obi298/Using-OTP-with-Python/assets/90945162/55524e58-6a85-4d05-9821-f01dc10131d0)



Here is a video of me using Microsoft Authenticator to scan the QR code. After scanning the code, a verification code pops up along with the username and issuer's name.










