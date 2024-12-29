
class Book:
    def __init__(self, title, author, isbn, copies):
        self.title = title
        self.author = author
        self.isbn = isbn
        self.copies = copies

    def display_info(self):
        return f"Title: {self.title}, Author: {self.author}, ISBN: {self.isbn}, Copies: {self.copies}"

    def borrow(self):
        if self.copies > 0:
            self.copies -= 1
            return True
        return False

    def return_book(self):
        self.copies += 1


class Member:
    def __init__(self, name, member_id):
        self.name = name
        self.member_id = member_id
        self.borrowed_books = []

    def borrow_book(self, book):
        if book.borrow():
            self.borrowed_books.append(book)
            print(f"{self.name} has borrowed {book.title}.")
        else:
            print(f"{book.title} is not available.")

    def return_book(self, book):
        if book in self.borrowed_books:
            book.return_book()
            self.borrowed_books.remove(book)
            print(f"{self.name} returned {book.title}.")
        else:
            print(f"{self.name} did not borrow {book.title}.")


class Library:
    def __init__(self):
        self.books = []
        self.members = []

    def add_book(self, title, author, isbn, copies):
        book = Book(title, author, isbn, copies)
        self.books.append(book)
        print(f"Book '{title}' added to the library.")

    def register_member(self, name, member_id):
        member = Member(name, member_id)
        self.members.append(member)
        print(f"Member '{name}' registered.")

    def display_books(self):
        print("\nLibrary Books:")
        for book in self.books:
            print(book.display_info())

    def find_book(self, title):
        for book in self.books:
            if book.title.lower() == title.lower():
                return book
        return None

    def display_members(self):
        print("\nLibrary Members:")
        for member in self.members:
            print(f"Name: {member.name}, ID: {member.member_id}")


def main():
    library = Library()

    while True:
        print("\nWelcome to the Library Management System")
        print("1. Register a member")
        print("2. Add a book ")
        print("3. Display All Books")
        print("4. Display All Members")
        print("5. Borrow a Book")
        print("6. Return a Book")
        print("7. Exit")

        choice = input("Enter your choice (1-7): ")

        if choice == "2":
            title = input("Enter book title: ")
            author = input("Enter book author: ")
            isbn = input("Enter book ISBN: ")
            copies = int(input("Enter number of copies: "))
            library.add_book(title, author, isbn, copies)

        elif choice == "1":
            name = input("Enter member name: ")
            member_id = input("Enter member ID: ")
            library.register_member(name, member_id)

        elif choice == "3":
            library.display_books()

        elif choice == "4":
            library.display_members()

        elif choice == "5":
            member_name = input("Enter your name: ")
            member = next((m for m in library.members if m.name == member_name), None)
            if not member:
                print(f"No member found with name '{member_name}'. Please register first.")
                continue

            book_title = input("Enter the title of the book you want to borrow: ")
            book = library.find_book(book_title)
            if book:
                member.borrow_book(book)
            else:
                print(f"Book '{book_title}' not found in the library.")

        elif choice == "6":
            member_name = input("Enter your name: ")
            member = next((m for m in library.members if m.name == member_name), None)
            if not member:
                print(f"No member found with name '{member_name}'.")
                continue

            book_title = input("Enter the title of the book you want to return: ")
            book = library.find_book(book_title)
            if book:
                member.return_book(book)
            else:
                print(f"Book '{book_title}' not found in the library.")

        elif choice == "7":
            print("Exiting the Library Management System.\n Thank you for visiting! \n gooddbye!")
            break

        else:
            print("Invalid choice. Please try again.")

class library mangement system:
    def __init__(self, root):
        self.root = root
        self.root.title("library mangement")
        self.root.geometry('5407x2359')
        self.root.cpngif(bg=
if __name__ == "__main__":
    main()
