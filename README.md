# Bank Management System

A simple yet functional Bank Management System implemented in C, designed to run on the terminal. This project demonstrates file handling, structured programming, and cross-platform development concepts.

## Features

- **Account Management**
  - Create new accounts with auto-generated account numbers
  - Secure PIN-based authentication with masked input
  - Support for Savings and Current account types

- **Banking Operations**
  - Deposit money
  - Withdraw money with minimum balance enforcement (₹2000)
  - Transfer funds between accounts
  - Check account balance
  - View complete transaction history

- **Security**
  - PIN masking during input (shows asterisks instead of digits)
  - 3-attempt login limit
  - Input validation for all operations

- **Cross-Platform Support**
  - Works on Windows (using `conio.h`)
  - Works on Mac/Linux (using `termios.h`)

## Architecture

The system uses a **dual-file CSV architecture**:

1. **`accounts_master.csv`** - Stores permanent account information
   - Account Number, Name, PIN, Account Type

2. **`transactions.csv`** - Maintains transaction history
   - Account Number, Transaction Type, Amount, Balance After Transaction

This separation keeps static data lightweight while allowing the transaction log to grow indefinitely.

## Installation & Usage

### On Mac/Linux:
```bash
gcc bank_management.c -o bank
./bank
```

### On Windows:
```bash
gcc bank_management_windows.c -o bank.exe
bank.exe
```

## Code Structure

- `initializeFile()` - Creates CSV files with headers if they don't exist
- `generateAccountNumber()` - Auto-generates unique account numbers
- `createAccount()` - Handles new account creation
- `login()` - Authenticates users with account number and PIN
- `depositMoney()` - Processes deposit transactions
- `withdrawMoney()` - Processes withdrawals with validation
- `transferMoney()` - Handles fund transfers between accounts
- `checkBalance()` - Displays current account balance
- `viewTransactions()` - Shows complete transaction history

## Known Limitations

- **PIN Storage**: PINs are stored in plaintext. In production, they should be hashed.
- **Float for Currency**: Uses `float` for monetary values, which can have precision issues. Should use integers (storing paise/cents) in real systems.
- **Account Number Generation**: Based on line count, can create duplicates if records are manually deleted.
- **Atomicity**: Transfer operations are not atomic. If the program crashes mid-transfer, money could be lost.

## Future Enhancements

- Encrypt PIN storage using hashing algorithms
- Use integers for currency (store values in paise)
- Add timestamp to transactions
- Implement proper database instead of CSV files
- Add transaction rollback mechanism
- Support for multiple account types (Fixed Deposit, etc.)

## Team

- **Person 1** - Architecture, File System, Platform Compatibility
- **Person 2** - Account Creation, Login, PIN Masking
- **Person 3** - Transfer Money Functionality
- **Person 4** - Balance Check, Transaction History
- **Person 5** - Deposit & Withdraw Operations

## License

This project is developed as an educational mini-project for learning C programming and file handling concepts.
