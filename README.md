# Bruteforce_stimulator_2.0
import itertools

# Define the character set and the target password
chardata = list("1234567890abcdefghijklmnopqrstuvwxyz")
password = input("Enter the password: ")

# Create a list to store all possible passwords
password_list = []

# Generate all possible combinations of characters up to the length of the target password
for length in range(1, len(password) + 1):
    for combination in itertools.product(chardata, repeat=length):
        possible_password = ''.join(combination)
        password_list.append(possible_password)

# Iterate over the list of possible passwords and check each one
attempts = 0
for attempt in password_list:
    attempts += 1
    if attempt == password:
        print(f"Password found after {attempts} attempts: {attempt}")
        break
    if attempts % 100000 == 0:
        print(f"Attempt {attempts}: Current guess is {attempt}")
else:
    print("Password not found in the generated combinations.")
