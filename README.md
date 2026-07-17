import base64

def protect_file(input_file, output_file):
    try:
        with open(input_file, "rb") as file:
            data = file.read()

        encoded_data = base64.b64encode(data)

        with open(output_file, "wb") as file:
            file.write(encoded_data)

        print("File protected successfully!")

    except FileNotFoundError:
        print("Input file not found.")

def restore_file(input_file, output_file):
    try:
        with open(input_file, "rb") as file:
            data = file.read()

        decoded_data = base64.b64decode(data)

        with open(output_file, "wb") as file:
            file.write(decoded_data)

        print("File restored successfully!")

    except FileNotFoundError:
        print("Input file not found.")

print("1. Protect File")
print("2. Restore File")

choice = input("Enter your choice (1/2): ")

if choice == "1":
    input_file = input("Enter input file name: ")
    output_file = input("Enter protected file name: ")
    protect_file(input_file, output_file)

elif choice == "2":
    input_file = input("Enter protected file name: ")
    output_file = input("Enter restored file name: ")
    restore_file(input_file, output_file)

else:
    print("Invalid choice!")