import java.util.ArrayList;
import java.util.Scanner;

class Expense {
    private String name;
    private double amount;

    public Expense(String name, double amount) {
        this.name = name;
        this.amount = amount;
    }

    public String getName() {
        return name;
    }

    public double getAmount() {
        return amount;
    }
}

public class ExpenseTracker {
    private ArrayList<Expense> expenses;

    public ExpenseTracker() {
        expenses = new ArrayList<>();
    }

    public void addExpense(String name, double amount) {
        Expense expense = new Expense(name, amount);
        expenses.add(expense);
        System.out.println("Expense added: " + name + " - $" + amount);
    }

    public void viewExpenses() {
        System.out.println("List of Expenses:");
        for (Expense expense : expenses) {
            System.out.println(expense.getName() + " - $" + expense.getAmount());
        }
    }

    public double calculateTotalExpenses() {
        double total = 0;
        for (Expense expense : expenses) {
            total += expense.getAmount();
        }
        return total;
    }

    public static void main(String[] args) {
        ExpenseTracker tracker = new ExpenseTracker();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("\nExpense Tracker Menu:");
            System.out.println("1. Add Expense");
            System.out.println("2. View Expenses");
            System.out.println("3. Calculate Total Expenses");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");

            int choice = scanner.nextInt();
            switch (choice) {
                case 1:
                    System.out.print("Enter expense name: ");
                    scanner.nextLine(); // Consume newline character
                    String name = scanner.nextLine();
                    System.out.print("Enter expense amount: ");
                    double amount = scanner.nextDouble();
                    tracker.addExpense(name, amount);
                    break;
                case 2:
                    tracker.viewExpenses();
                    break;
                case 3:
                    System.out.println("Total Expenses: $" + tracker.calculateTotalExpenses());
                    break;
                case 4:
                    System.out.println("Exiting...");
                    System.exit(0);
                default:
                    System.out.println("Invalid choice. Please enter a valid option.");
            }
        }
    }
}
