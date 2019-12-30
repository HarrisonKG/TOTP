Kristen Harrison  
TOTP implementation in Python  
  
  
  
  
To generate the QR code, run:  
	python3 prob2.py --generate-qr  
  
(this will save a PNG file of the QR code in the same directory as the program)  
  
My implementation uses Python's qrcode library to create the image, then saves it  
  
  
  
  
To generate the TOTP codes, run:  
	python3 prob2.py --get-otp  
   
(this will print a verification code every 30 seconds from the time you run the program)  
  
My implementation follows the workflow laid out in RFC4226 - HOTP which is the key building block of TOTP. The organization is   
  
Step 1: generate HMAC-SHA-1(K,T)  
Step 2: truncate the resulting 20-byte string to a 4-byte string  
Step 3: Compute the TOTP value by modding the truncated string by 10^6 to get a 6-digit passcode  
  
I use the time, math, hmac, base64, and struct libraries to convert my key and time_factor variables into bytestrings and calculate the hmac-sha-1 value.  
  
I use python array manipulation and bitmasking to truncate the string to 4 bytes.  
  
And I use the struct library to convert the result back to an int and perform bitmasking and modulo operations to calculate the final 6-digit passcode value.  
  
The code is liberally commented to explain each step of the way.  
