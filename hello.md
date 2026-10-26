# I am learning to use git!
import string
import random

# Ask user whether to encode (0) or decode (1)
choice = int(input("Enter 0 to encode or 1 to decode: "))

# Ask the user for input
original = input("Enter your message: ").strip()
words = original.split()
result = []

# Encoding function
def encoding():
    for word in words:
        if len(word) >= 3:
            # Move the first character to the end
            modified = word[1:] + word[0]

            # Add 3 random letters at the beginning and end
            prefix = ''.join(random.choices(string.ascii_lowercase, k=3))
            suffix = ''.join(random.choices(string.ascii_lowercase, k=3))

            # Final encoded word
            encoded_word = prefix + modified + suffix
            result.append(encoded_word)
        else:
            # Reverse short words
            result.append(word[::-1])
    
    # Show encoded message
    print("\n🔐 Encoded Message:")
    print(" ".join(result))

# Decoding function
def decoding():
    for word in words:
        if len(word) >= 3:
            # Strip first and last 3 characters (random padding)
            trimmed = word[3:-3]

            # Move last character to the front
            decoded_word = trimmed[-1] + trimmed[:-1]
            result.append(decoded_word)
        else:
            # Reverse short words
            result.append(word[::-1])
    
    # Show decoded message
    print("\n🔓 Decoded Message:")
    print(" ".join(result))

# Run based on user input

if choice == 0:
    encoding()
elif choice == 1:
    decoding()
else:
    print("❌ Invalid choice! Please enter 0 to encode or 1 to decode.")
        
