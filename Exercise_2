import os
import re 

CONTACTS_FILE = "contacts.txt"

class Contact:
    def __init__(self, name, phone):
        self.name = name
        self.phone = phone

    def __str__(self):
        # print(contact) 했을 때 보기 좋게 출력
        return f"{self.name},{self.phone}"

    @staticmethod #Contact 인스턴스 없을경우(첫 호출) 사용하기 위한 정적 메서드
    def from_string(line):
        name, phone = line.strip().split(",")
        return Contact(name, phone)

# Add Contacts
def add_contacts(contacts):
    #이름 유효성 검사 루프(중복 이름값 존재 방지)
    while True:
        name = input("Enter name : ")
        if name in contacts:
            print(f"'{name}' is already in contacts. Please use a different name.")
        else:
            break
    #전화번호 유효성 검사 루프 (ex.010-xxxx-xxxx)
    while True:
        phone = input("Enter phone number (010-xxxx-xxxx): ")
        if re.fullmatch(r"010-\d{4}-\d{4}", phone):
            break
        else:
            print("Invalid format. Please use 010-0000-0000 format.")
    contacts[name] = Contact(name, phone)

# Search Contacts
def search_contacts(contacts):
    name = input("Enter the name to search : ")
    contact = contacts.get(name)
    if name in contacts.keys():
        print(f"{name}'s contact : {contact.phone}")
    else: #search 대상 이름이 없을 경우
        print(f"Sorry. {name} is not in Contacts file.")

# Load Contacts
def load_contacts():
    try:
        with open(CONTACTS_FILE, "r") as f:
            data = {}
            for line in f:
                contact = Contact.from_string(line)
                data[contact.name] = contact
            return data
    except FileNotFoundError:
        return {}

# Save Contacts
def save_contacts(contacts):
    with open(CONTACTS_FILE, "w") as f:
        for contact in contacts.values():
            f.write(str(contact)+"\n")

# View Contacts
def view_contacts(contacts):
    #dict이 존재하지 않을 경우
    if not contacts:
        print("Sorry. No contacts found.")
    else:
        print("Contact List:")
        for contact in contacts.values(): 
            print(f"name : {contact.name:^5} | contacts : {contact.phone:^15}")

def main():
    contacts = load_contacts()
    print("\n***Data&AI Exercise2***")
    while True:
        print("\nMenu:")
        print("1. Add Contact")
        print("2. View Contacts")
        print("3. Search Contact")
        print("4. Quit\n")
        choice = input("Choose an option (1-4): ")

        if choice == "1":
            add_contacts(contacts)
            print("Contact added.")
        elif choice == "2":
            view_contacts(contacts)
        elif choice == "3":
            search_contacts(contacts)
        elif choice == "4":
            save_contacts(contacts)
            print("Contacts saved. Goodbye!")
            break
        else:
            if (choice.isnumeric()==False):
                print("Invalid type. Please enter number.")   
            else:
                print("Invalid number. Please enter 1-4.")

if __name__ == "__main__":
    main()
