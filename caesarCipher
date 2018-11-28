# A Caesar Cipher with a twist
# Take position in string, if index=0 position, shift 7, if index=1 position shift 4, if index=2, shift 16, and it can loop. 
# After the third character, if the position is odd, then divid by 3, floored. if Even, divid by 2 then shift by that.
# Case will be preserved, and characters other than letters will have their value shifted by their index. 

# ord(char) -> int # Character to ASCII character
# chr(int) -> char # ASCII value to character
# Min/Max for letters in ASCII
# a = 97 z = 122 
# A = 65 Z = 90
import math # math library, used for the floor function

def encode(inputString): # Method for encoding a plan text string. 
	rv = "" # return value
	count = 0; # variable used to keep track of the indec
	for c in inputString: # Loop for each character c in the string inputString
		if c.isalpha(): # If c is a letter
			if c.isupper(): # If c is upper case
				# Set the min and max for the range of uppercase letters in ascii
				max = 90
				min = 65
			else: # c is lower
				# Set the min and max for the range of lowercase letters in ascii
				max = 122
				min = 97

			if count == 0: # index 0, shift by 7
				dec = ord(c) + 7
				
				if dec > max: # Check if over max ascii value
					dec  = (dec - max) + min # if over, subtract the max from the shifted value and add to min

				rv = rv + chr(dec) # add new encoded character to the return value

			elif count == 1: # Same process as for index 0, but shifting by 4
				dec = ord(c) + 4
				
				if dec > max:
					dec  = (dec - max) + min

				rv = rv + chr(dec)

			elif count == 2:
				dec = ord(c) + 16 # Same process as for index 0, but shifting by 16
				
				if dec > max:
					dec  = (dec - max) + min

				rv = rv + chr(dec)

			else: # if not one of the first 3 characters
				
				if count % 2 == 0: # check if value is even 
					
					dec = ord(c) + math.floor(count / 2) # if even, then shift by the index divided by 2

					# Check if over
					if dec > max:
						dec  = (dec - max) + min

					rv = rv + chr(dec)
				else:
					
					dec = ord(c) + math.floor(count / 3) # if odd, then shift by the index divided by 3
					# Check if over
					if dec > max:
						dec  = (dec - max) + min

					rv = rv + chr(dec)
		else: # Not a letter
			if ord(c) + count < 65: # if shifting by the index doesn't make this non-letter into a letter
				rv = rv + chr(ord(c) + count) # shift by the index
			else: # shifting by the index would make a non-letter into a letter
				rv = rv + c # add the character to the return value
				

		count = count + 1 # add one to index tracker

	return rv


def decode(inputString): # Method for decoding an encoded string. 
	# Comments in this method will be less frequent, this is doing the encode in reverse. 
	rv = "" # Return Value
	count = 0 # Index tracker 
	for c in inputString: # Loop for each character c in the string inputString
		if c.isalpha(): # If c is a letter
			if c.isupper(): # If c is upper case
				# Set the min and max for the range of uppercase letters in ascii
				max = 90
				min = 65
			else: # c is lower
				# Set the min and max for the range of lowercase letters in ascii
				max = 122
				min = 97

			if count == 0: # index 0, shift by 7
				dec = ord(c) - 7
				
				if dec < min: # Check if under min ascii value
					dec  = max - (min - dec) # if under, from the max subtract the min minus the shifted value

				rv = rv + chr(dec) # add decoded character to the return value

			elif count == 1:
				dec = ord(c) - 4
				
				if dec < min:
					dec  = max - (min - dec)

				rv = rv + chr(dec)

			elif count == 2:
				dec = ord(c) - 16
				
				if dec < min:
					dec  = max - (min - dec)

				rv = rv + chr(dec)

			else: # if not one of the first 3 characters
				
				if count % 2 == 0: # check if value is even 
					
					dec = ord(c) - math.floor(count / 2) # if even, then shift by the index divided by 2
					
					if dec < min:
						dec  = max - (min - dec)

					rv = rv + chr(dec)
				else: # odd
					
					dec = ord(c) - math.floor(count / 3)
					if dec < min:
						dec  = max - (min - dec)

					rv = rv + chr(dec)

		else: # Not a letter
			if ord(c) - count >= 32: # if shifting by the index doesn't make this non-letter into a letter
				rv = rv + chr(ord(c) - count)
			else:
				rv = rv + c

		count = count + 1

	return rv

def runCode():
	runAgain = True
	while runAgain:
		print("Welcome to Igor's Caesar Cipher. Please enter a string to encode:")
		plainText = input()
		print("Your plain text string is: " + plainText)
		encodedText = encode(plainText)
		print("Your encoded string is: " + encodedText)
		decodedText = decode(encodedText)
		print("Your encoded string after being decoded is: " + decodedText)
		if input("Run again?(y/n)") == "n" :
			runAgain = False
	

runCode()
