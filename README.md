# Input space-separated ASCII values
ascii_input = input("Enter ASCII numbers separated by space: ")

# Convert them into characters
chars = ''.join([chr(int(num)) for num in ascii_input.split()])

direction=input("Type 'ENCODE' to encrypt or 'DECODE' to decrypt:\n")
text=input("Type your message:")
shift=int(input("Type the shift number:"))

#Encodes (Encrypts): shifts letters and gives their SHIFTEF code.
#FOR BETTER UNDERSTANDING I'M USING CHATGPT
#Decodes (Decrypts): reverses the shift and shows original text
def encode(text,shift):
    result=''
    for char in text:
        if char.isalpha():# Determine base ASCII (A or a) for correct wrapping
            base=ord('A')if char.isupper() else ord('a')
            shifted=(ord(char)-base+shift) %26+base
            result+=chr(shifted)
        else:
            result+=char
    return result
     
if direction == 'ENCODE':
    encoded_text=encode(text,shift)
    print("Encoded text:",encoded_text)

if direction=='DECODE':
    decoded_text=encode(text,-shift)
    print("Decoded text:",decoded_text)

