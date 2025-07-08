# Woolf University. Python Programing Course. Homework – Advanced Object-Oriented Programming in Python

## Overview

This assignment builds on your previous AddressBook project. You will enhance the data model with a `Birthday` field and integrate birthday-related functionality (e.g., upcoming birthdays). You will also extend the CLI assistant with new commands to manage birthdays.

---

## Task 1: Extend Data Model

1. **Birthday Field**

   * Create a `Birthday` class inheriting from `Field`.
   * Accepts a date string in `DD.MM.YYYY` format.
   * Validates and converts to a `datetime.date` object in `__init__`.
   * Raises `ValueError("Invalid date format. Use DD.MM.YYYY")` on invalid input.

2. **Record Class**

   * Add attribute `self.birthday: Birthday | None`, initialized to `None`.
   * Implement method `add_birthday(self, value: str) -> None`:

     * Creates a `Birthday(value)` and assigns to `self.birthday`.
     * Raises appropriate errors on invalid format.

3. **Validation**

   * Ensure existing `Phone` class still enforces exactly 10 digits.
   * Add input validation in `Birthday` class as specified.

4. **Upcoming Birthdays**

   * Integrate the `get_upcoming_birthdays` function (from previous homework) into the `AddressBook` class.
   * `AddressBook.upcoming_birthdays() -> List[dict]` returns users to congratulate over the next 7 days (including today), shifting weekend birthdays to Monday.

5. **Switch to AddressBook**

   * Modify your CLI assistant to use a `book = AddressBook()` instance instead of a simple `contacts` dict.

---

## Task 2: CLI Handlers for Birthday Commands

Implement the following command handlers, decorated with `@input_error`:

1. **`add-birthday [name] [DD.MM.YYYY]`**

   * Adds or updates the `birthday` for the given contact.

2. **`show-birthday [name]`**

   * Displays the birthday of the specified contact.
   * If missing, informs the user.

3. **`birthdays`**

   * Lists contacts whose birthdays occur in the next 7 days, showing each name and scheduled congratulation date.

```python
@input_error
def add_birthday(args: list[str], book: AddressBook) -> str:
    # implementation

@input_error
def show_birthday(args: list[str], book: AddressBook) -> str:
    # implementation

@input_error
def birthdays(args: list[str], book: AddressBook) -> str:
    # implementation
```

### Final Supported Commands

Below are the bot’s supported commands along with their descriptions:

* `add [name] [phone]`
  Add a new contact or add a phone number to an existing contact.

* `change [name] [old_phone] [new_phone]`
  Replace an existing phone number for the specified contact.

* `phone [name]`
  Display all phone numbers for the given contact.

* `all`
  List all contacts in the address book with their phone numbers and birthdays (if set).

* `add-birthday [name] [DD.MM.YYYY]`
  Add or update the birthday for the specified contact.

* `show-birthday [name]`
  Show the birthday date of the given contact or inform if none is set.

* `birthdays`
  List contacts whose birthdays fall within the next 7 days (including today), shifting weekend birthdays to the next Monday, along with the congratulation date.

* `hello`
  The bot greets you: "How can I help you?"

* `close` / `exit`
  Terminate the bot with a farewell message.

---

## Evaluation Criteria

1. **Functionality**: All listed commands work as specified.
2. **Data Formatting**: Outputs are user-friendly and clear.
3. **Validation & Error Handling**: Informative messages for invalid input, missing contacts, etc.

   * Date format: `DD.MM.YYYY`.
   * Phone format: exactly 10 digits.
4. **Graceful Exit**: Bot terminates cleanly on `close` or `exit`.
5. **Code Quality**: Classes and methods are well-documented, follow PEP8, and use OOP principles.
