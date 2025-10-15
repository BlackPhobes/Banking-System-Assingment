# Banking-System-Assingment
This banking system compiled by C++ , contains the basics of programming ,you can login , select the type of activity you'd like to do on the the app , Wherether you want to withdraw , make a deposit or transfer money , you can also exit the application once done using it .
#include <iostream>
using namespace std;

// Global variables
string username = "Tha";
string password = "123";
string uname;
string psw;
double balance = 10000.00;

// Function declarations
void welcome()
{
    cout << "You have logged in successfully!\n\n";
}

bool Login()
{
    cout << "Enter Username: ";
    cin >> uname;
    cout << "Enter your password: ";
    cin >> psw;

    if (uname == username && psw == password) {
        welcome();
        return true;
    } else {
        cout << "Invalid username or password. Access denied.\n";
        return false;
    }
}

void CheckBalance()
{
    cout << "Current Account Balance: R" << balance << "\n\n";
}

void Deposit()
{
    double amountToDeposit;
    cout << "Enter Deposit Amount: ";
    cin >> amountToDeposit;

    if (amountToDeposit <= 0) {
        cout << "Invalid deposit amount.\n\n";
        return;
    }

    balance += amountToDeposit;
    cout << "Deposit successful!\n";
    cout << "New Balance: R" << balance << "\n\n";
}

void Withdraw()
{
    double amountToWithdraw;
    cout << "Enter Withdrawal Amount: ";
    cin >> amountToWithdraw;

    if (amountToWithdraw <= 0) {
        cout << "Invalid withdrawal amount.\n\n";
        return;
    }

    if (amountToWithdraw > balance) {
        cout << "Insufficient balance.\n\n";
        return;
    }

    balance -= amountToWithdraw;
    cout << "Withdrawal successful!\n";
    cout << "Remaining Balance: R" << balance << "\n\n";
}

void SendMoney()
{
    string recipientName;
    cout << "Recipient's Name: ";
    cin >> recipientName;

    double amountToTransfer;
    cout << "Enter Transfer Amount: ";
    cin >> amountToTransfer;

    if (amountToTransfer <= 0) {
        cout << "Invalid transfer amount.\n\n";
        return;
    }

    if (amountToTransfer > balance) {
        cout << "Insufficient balance to transfer.\n\n";
        return;
    }

    balance -= amountToTransfer;
    cout << "Transfer successful to " << recipientName << ".\n";
    cout << "Remaining Balance: R" << balance << "\n\n";
}

// Main function - program entry point
int main()
{
    // Login first
    if (!Login()) {
        return 0; // Exit if login fails
    }

    int selection;

    // Menu loop
    do {
        cout << "***** Banking Menu *****\n";
        cout << "1. Check Balance\n";
        cout << "2. Deposit\n";
        cout << "3. Withdraw\n";
        cout << "4. Send Money\n";
        cout << "5. Exit\n";
        cout << "Make A Selection: ";
        cin >> selection;

        cout << endl;

        switch (selection) {
            case 1:
                CheckBalance();
                break;
            case 2:
                Deposit();
                break;
            case 3:
                Withdraw();
                break;
            case 4:
                SendMoney();
                break;
            case 5:
                cout << "Thank you for banking with us. Goodbye!\n";
                break;
            default:
                cout << "Invalid choice, please try again.\n\n";
        }
    } while (selection != 5);

    return 0;
}
