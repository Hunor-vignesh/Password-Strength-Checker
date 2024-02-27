import re

def password_strength(password):
    # Length check
    if len(password) < 8:
        return "Weak: Password must be at least 8 characters long."

    # Check for uppercase letters
    if not any(char.isupper() for char in password):
        return "Weak: Password must contain at least one uppercase letter."

    # Check for lowercase letters
    if not any(char.islower() for char in password):
        return "Weak: Password must contain at least one lowercase letter."

    # Check for digits
    if not any(char.isdigit() for char in password):
        return "Weak: Password must contain at least one digit."

    # Check for special characters
    special_characters = re.compile('[@_!#$%^&*()<>?/\|}{~:]')
    if not special_characters.search(password):
        return "Weak: Password must contain at least one special character."

    return "Strong: Password meets all criteria."

# Test the function
password = input("Enter your password: ")
print(password_strength(password))
