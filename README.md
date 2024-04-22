# Using OTP with Python

<br>
<br>
<br>

# Introduction

One-Time Password(OTP) is a password that is used for one login session on a user's device. OTPs can be delivered to users through text messages, authenticator apps, email, and more. It can be used as an additional layer of security for users to confirm their identities. PyOTP is a Python library that is used to generate and verify one-time passwords. It is used to implement MFA solutions in login systems.
The purpose of this lab was to learn about how 2FA solutions are used in the real world. 

<br>
<br>
<br>

# Technologies Used

- Python
- Authenticator App (Microsoft Authenticator)

<br>
<br>
<br>

# Project

I first installed the required libraries for this project. The required libraries for this project were, **pyotp**, **qrcode**, **getpass** and **time**.


**pyotp:** Generates and verifies one-time passwords.

**qrcode:** Creates a qrcode for user to scan with authenticator app.

**getpass:** Encrypts the password when user inputs it.

**time:** Creates a time based sequence for verification.

<br>

```
pip install pyotp
pip install qrcode
pip install getpass
pip install time
```


Then I imported the libraries in the first lines of this project. 

```
import pyotp
import qrcode
import getpass
import time

key = pyotp.random_base32()

print(key)
```

I was able to generate a random secret key which was used for the next code. The secret key changes everytime the code is executed.

![1](https://github.com/obi298/Using-OTP-with-Python/assets/90945162/4472bad2-8a11-462c-b559-fc89b3b5b642)

<br>
<br>

In this step, I entered the secret key which was generated from the previous code. 

```
key = ''

totp = pyotp.TOTP(key)
```


![2](https://github.com/obi298/Using-OTP-with-Python/assets/90945162/1d72f98f-72c4-4015-8f1a-1d87ff79aa48)



<br>

I then created the username and issuer name which was displayed on the authenticator app. 

<br>

```
uri = pyotp.totp.TOTP(key).provisioning_uri(name= "user", issuer_name= "Company" )
print(uri)

qrcode.make(uri)
```
<br>
<br>

I was able to create a provisioning URI and generate a QR code which was scanned with my mobile authenticator app. The provisioning URI is used to deliver a verification token to a new user or device. 


As you can see from this image, the URI contains the following paremeters:
<br>

**otpauth://:** Specifies that this URI is for OTP authentication.

**totp:** Specifies that this verification is time-based.

**issuer:** The name of the application or service generating the token.

**name:** The name of the user.

**secret:** Random secret key used to generate a verification code.

<br>
<br>

![4](https://github.com/obi298/Using-OTP-with-Python/assets/90945162/55524e58-6a85-4d05-9821-f01dc10131d0)



I decided to use Microsoft Authenticator for this project. After scanning the QR code, a verification code popped up along with the username and issuer's name.
<br>

<img src="https://github.com/obi298/Using-OTP-with-Python/assets/90945162/fe77be7b-65f5-4221-ba76-56e91dad434e" alt="First Scan Research" width="400" height="700">



<br>
<br>
<br>

# Conclusion








