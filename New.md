#skyairlines

import java.util.Scanner;

class Customer {
	private String name;
	private String source;
	private String destination;

	public Customer(String name, String source, String destination) {
		this.name = name;
		this.source = source;
		this.destination = destination;
	}

	public String getName() {
		return name;
	}

	public String getSource() {
		return source;
	}

	public String getDestination() {
		return destination;
	}
}

class SkyAirlines {
	public void printMessage(Customer customer) {
		System.out.println("Dear " + customer.getName() + ", welcome onboard with service from " + customer.getSource()
				+ " to " + customer.getDestination() + ". Thankyou for choosing Sky Airlines. Enjoy your flight.");
	}
}

public class UserInterface {
	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);

		System.out.println("Enter name");
		String name = scanner.nextLine();

		System.out.println("Enter source");
		String source = scanner.nextLine();

		System.out.println("Enter destination");
		String destination = scanner.nextLine();

		Customer customer = new Customer(name, source, destination);
		SkyAirlines skyAirlines = new SkyAirlines();
		skyAirlines.printMessage(customer);
	}
}

##smallest of three numbers

import java.util.Scanner;

public class UserInterface {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.println("Enter the numbers:");
        int num1 = scanner.nextInt();
        int num2 = scanner.nextInt();
        int num3 = scanner.nextInt();
        
        if (num1 == num2 && num2 == num3) {
            System.out.println("All numbers are equal");
        } else {
            int smallest = (num1 < num2) ? 
                           ((num1 < num3) ? num1 : num3) : 
                           ((num2 < num3) ? num2 : num3);
            System.out.println("The smallest number is " + smallest);
        }
        
        scanner.close();
    }
}


##swap two numbers

import java.util.Scanner;

class NumberSwapper {
	private int first;
	private int second;

	public void setNumbers(int first, int second) {
		this.first = first;
		this.second = second;
	}

	public void swap() {
		first = first ^ second;
		second = first ^ second;
		first = first ^ second;
	}

	public void display() {
		System.out.println("Before swapping");
		System.out.println("first = " + first + ", second = " + second);
		swap();
		System.out.println("After swapping");
		System.out.println("first = " + first + ", second = " + second);
	}
}

public class UserInterface {
	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
		NumberSwapper swapper = new NumberSwapper();

		System.out.println("Enter the numbers");
		int first = scanner.nextInt();
		int second = scanner.nextInt();

		swapper.setNumbers(first, second);
		swapper.display();
	}
}



