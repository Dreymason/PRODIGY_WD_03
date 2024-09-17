import re

def assess_password_strength(password):
    # Creating the strength score
    strength_score = 0
    feedback = []

    # Initialising the length of the password
    if len(password) >= 8:
        strength_score += 1
    else:
        feedback.append("Password should be at least 8 characters long.")

    # Minimum numbers for uppercase and lowercase letters
    if re.search(r'[A-Z]', password):
        strength_score += 1
    else:
        feedback.append("Password should contain at least one uppercase letter.")

    if re.search(r'[a-z]', password):
        strength_score += 1
    else:
        feedback.append("Password should contain at least one lowercase letter.")

    # Checks for numbers
    if re.search(r'[0-9]', password):
        strength_score += 1
    else:
        feedback.append("Password should contain at least one number.")

    # Initialising that at least one special characters must be added
    if re.search(r'[!@#$%^&*(),.?":{}|<>]', password):
        strength_score += 1
    else:
        feedback.append("Password should contain at least one special character (!@#$%^&*() etc.).")

    # This provide freedback based on strength score
    if strength_score == 5:
        feedback.append("Your password is strong.")
    elif strength_score >= 3:
        feedback.append("Your password is medium strength.")
    else:
        feedback.append("Your password is weak.")

    return strength_score, feedback
print()
def password_strength_tool():
    print("Password Strength Assessment Tool")
    password = input("Enter your password: ")
    
    strength_score, feedback = assess_password_strength(password)
    print()
    print(f"\nPassword Strength Score: {strength_score}/5")
    for comment in feedback:
        print(f"- {comment}")

if __name__ == "__main__":
    password_strength_tool()
