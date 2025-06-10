import java.util.Scanner;

// Define ATM interface
interface ATMInterface {
int balanceEnquiry();
int withdraw(int amount);
void deposit(int amount);
}

// Implementing the ATM interface

class UserAccount implements ATMInterface {
private int balance = 0;

public int balanceEnquiry() {  
    return balance;  
}  

public int withdraw(int amount) {  
    if (amount <= 0 || amount % 100 != 0) {  
        System.out.println("INVALID AMOUNT. PLEASE ENTER A POSITIVE VALUE IN MULTIPLES OF 100.");  
        return 0;  
    }  

    if (balance >= amount) {  
        balance -= amount;  
        return amount;  
    } else {  
        System.out.println("INSUFFICIENT BALANCE. YOUR CURRENT BALANCE IS: ₹" + balance);  
        return 0;  
    }  
}  

public void deposit(int amount) {  
    if (amount <= 0 || amount % 100 != 0) {  
        System.out.println("INVALID AMOUNT. PLEASE ENTER A POSITIVE VALUE IN MULTIPLES OF 100.");  
        return;  
    }  
    balance += amount;  
    System.out.println("DEPOSITED SUCCESSFULLY.");  
}

}

// Main class
public class Task3ATMProgram {
public static void main(String[] args) {
Scanner s = new Scanner(System.in);
int amt, res;

ATMInterface user = new UserAccount();  

    while (true) {  
        System.out.println("\n1. WITHDRAW\n2. DEPOSIT\n3. BALANCE ENQUIRY");  
        System.out.print("ENTER YOUR CHOICE: ");  
        int ch = s.nextInt();  

        switch (ch) {  
            case 1:  
                System.out.print("ENTER AMOUNT TO WITHDRAW (MULTIPLES OF 100): ");  
                amt = s.nextInt();  
                res = user.withdraw(amt);  
                if (res != 0) {  
                    System.out.println("COLLECT THE CASH: ₹" + res);  
                }  
                break;  
            case 2:  
                System.out.print("ENTER AMOUNT TO DEPOSIT (MULTIPLES OF 100): ");  
                amt = s.nextInt();  
                user.deposit(amt);  
                break;  
            case 3:  
                System.out.println("YOUR CURRENT BALANCE IS: ₹" + user.balanceEnquiry());  
                break;  
            default:  
                System.out.println("INVALID CHOICE. PLEASE SELECT AGAIN.");  
        }  

        System.out.print("DO YOU WANT TO PERFORM ANOTHER TRANSACTION? (YES/NO): ");  
        String c = s.next();  
        if (c.equalsIgnoreCase("no")) {  
            break;  
        }  
    }  

    System.out.println("THANK YOU FOR USING THE ATM.");  
    System.out.println("HAVE A NICE DAY!");  

    s.close();  
}

}

 
