import random

def get_computer_choice():
    return random.choice(["rock", "paper", "scissors"])

def get_user_choice():
    while True:
        choice = input("Choose rock, paper, or scissors: ").lower()
        if choice in ["rock", "paper", "scissors"]:
            return choice
        else:
            print("Invalid input. Please try again.")

def determine_winner(user, computer):
    if user == computer:
        return "tie"
    elif (user == "rock" and computer == "scissors") or \
         (user == "scissors" and computer == "paper") or \
         (user == "paper" and computer == "rock"):
        return "user"
    else:
        return "computer"

def play_game():
    print("=== Welcome to Rock, Paper, Scissors ===")
    user_score = 0
    computer_score = 0
    round_number = 1

    while True:
        print(f"\n--- Round {round_number} ---")
        user_choice = get_user_choice()
        computer_choice = get_computer_choice()

        print(f"You chose: {user_choice}")
        print(f"Computer chose: {computer_choice}")

        winner = determine_winner(user_choice, computer_choice)

        if winner == "tie":
            print("It's a tie!")
        elif winner == "user":
            print("You win this round!")
            user_score += 1
        else:
            print("Computer wins this round!")
            computer_score += 1

        print(f"Score - You: {user_score}, Computer: {computer_score}")

        play_again = input("\nDo you want to play another round? (yes/no): ").lower()
        if play_again != "yes":
            print("\nThanks for playing! Final Score:")
            print(f"You: {user_score} | Computer: {computer_score}")
            break

        round_number += 1

# Start the game
play_game()

task 5ontacts = []

def add_contact():
    print("\n--- Add New Contact ---")
    name = input("Enter name: ")
    phone = input("Enter phone number: ")
    email = input("Enter email: ")
    address = input("Enter address: ")
    
    contact = {
        "name": name,
        "phone": phone,
        "email": email,
        "address": address
    }
    contacts.append(contact)
    print("Contact added successfully!")

def view_contacts():
    print("\n--- Contact List ---")
    if not contacts:
        print("No contacts found.")
    else:
        for idx, contact in enumerate(contacts, start=1):
            print(f"{idx}. {contact['name']} - {contact['phone']}")

def search_contact():
    print("\n--- Search Contact ---")
    query = input("Enter name or phone number to search: ").lower()
    found = False
    for contact in contacts:
        if query in contact["name"].lower() or query in contact["phone"]:
            print(f"\nName: {contact['name']}")
            print(f"Phone: {contact['phone']}")
            print(f"Email: {contact['email']}")
            print(f"Address: {contact['address']}")
            found = True
    if not found:
        print("No matching contact found.")

def update_contact():
    print("\n--- Update Contact ---")
    name = input("Enter the name of the contact to update: ").lower()
    for contact in contacts:
        if contact["name"].lower() == name:
            print("Leave blank to keep current value.")
            new_phone = input(f"New phone ({contact['phone']}): ") or contact["phone"]
            new_email = input(f"New email ({contact['email']}): ") or contact["email"]
            new_address = input(f"New address ({contact['address']}): ") or contact["address"]
            contact["phone"] = new_phone
            contact["email"] = new_email
            contact["address"] = new_address
            print("Contact updated successfully!")
            return
    print("Contact not found.")

def delete_contact():
    print("\n--- Delete Contact ---")
    name = input("Enter the name of the contact to delete: ").lower()
    for contact in contacts:
        if contact["name"].lower() == name:
            contacts.remove(contact)
            print("Contact deleted successfully!")
            return
    print("Contact not found.")

def main_menu():
    while True:
        print("\n====== Contact Management System ======")
        print("1. Add Contact")
        print("2. View Contact List")
        print("3. Search Contact")
        print("4. Update Contact")
        print("5. Delete Contact")
        print("6. Exit")

        choice = input("Choose an option (1-6): ")

        if choice == '1':
            add_contact()
        elif choice == '2':
            view_contacts()
        elif choice == '3':
            search_contact()
        elif choice == '4':
            update_contact()
        elif choice == '5':
            delete_contact()
        elif choice == '6':
            print("Exiting Contact Management System. Goodbye!")
            break
        else:
            print("Invalid option. Please try again.")
main_menu()

