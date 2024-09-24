# Password-Generator

import random
import string

def generate_password(length=12, use_alphabets=True, use_digits=True, use_special_symbols=True):
    character_pool = ''
    
    if use_alphabets:
        character_pool += string.ascii_letters  
    if use_digits:
        character_pool += string.digits  
    if use_special_symbols:
        character_pool += string.punctuation  
    
    if not character_pool:
        raise ValueError("At least one type of character (alphabets, digits, or special symbols) must be selected.")
    
    password = ''.join(random.choices(character_pool, k=length))
    return password

def ask_user_preferences():
    use_alphabets = input("Do you want alphabets in your password? (yes/no): ").strip().lower() == 'yes'
    use_digits = input("Do you want digits in your password? (yes/no): ").strip().lower() == 'yes'
    use_special_symbols = input("Do you want only special symbols (e.g., !, @, #) in your password? (yes/no): ").strip().lower() == 'yes'
    
    length = int(input("Enter the desired length of the password: "))
    
    return generate_password(length, use_alphabets, use_digits, use_special_symbols)

if __name__ == "__main__":
    try:
        password = ask_user_preferences()
        print("Generated Password:", password)
    except ValueError as e:
        print("Error:", e)
