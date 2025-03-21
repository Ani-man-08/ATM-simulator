import java.util.Scanner;
public class project_ATM {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        double balance = 10000.00;
        int pin = 1234;
        int attempts = 3;
        System.out.println("Welcome to our ATM System.");
        while (attempts > 0) {
            System.out.print("Enter your pin: ");
            int pin1 = sc.nextInt();
            if (pin1 == pin) {
                System.out.println("login success !");
                break;
            } else {
                attempts--;
                System.out.println("Wrong pin!! you have " + attempts + " left.");
                if (attempts == 0) {
                    System.out.println("Too many failed attempts.");
                    sc.close();
                    return;
                }
            }
        }
        while (true) {
            System.out.println("\nATM menu");
            System.out.println("1.Check Balance");
            System.out.println("2.Deposit Money");
            System.out.println("3.Withdraw Money");
            System.out.println("4.Exit");
            System.out.println("Choose an option: ");
            int choice = sc.nextInt();
            switch (choice) {
                case 1:
                    System.out.println("Your current balance is: Rs." + balance);
                    break;

                case 2:
                    System.out.println("Enter deposit amount: ");
                    double deposit = sc.nextDouble();
                    if (deposit > 0) {
                        deposit += balance;
                        System.out.println("Total balance is: Rs." + deposit);
                    } else {
                        System.out.println("Invalid amount");
                    }
                    break;

                case 3:
                    System.out.println("Enter withdrawal amount");
                    double withdraw = sc.nextDouble();
                    if (withdraw > 0 && withdraw <= balance) {
                        withdraw -= balance;
                        System.out.println("Total balance is: Rs." + withdraw);
                    } else if (withdraw <= 0) {
                        System.out.println("invalid amount");
                    } else {
                        System.out.println("Insufficient Balance");
                    }
                    break;

                case 4:
                    System.out.println("Thankyou For wisiting!!");
                    sc.close();
                    return;
                default:
                    System.out.println("invalid command ,please try again.");
            }
        }
    }
}
