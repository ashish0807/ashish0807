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


##oxygen plants

import java.util.Scanner;

class OxygenProduction {
    private double length;
    private double breadth;
    private double plantArea;

    public OxygenProduction(double length, double breadth, double plantArea) {
        this.length = length;
        this.breadth = breadth;
        this.plantArea = plantArea;
    }

    public void calculate() {
        if (length <= 0) {
            System.out.println("Invalid length");
            return;
        }
        if (breadth <= 0) {
            System.out.println("Invalid breadth");
            return;
        }
        if (plantArea <= 0) {
            System.out.println("Invalid plant area");
            return;
        }

        double roomArea = length * breadth; 
        double plantAreaInM2 = plantArea / 10000; 
        int totalPlants = (int) (roomArea / plantAreaInM2);

        totalPlants = (totalPlants / 10) * 10; 

        double totalOxygen = totalPlants * 0.9; 

        System.out.println("Total number of plants is " + totalPlants);
        System.out.printf("Total oxygen production is %.2f litres\n", totalOxygen);
    }
}

public class UserInterface {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter the length of the room(in m)");
        double length = scanner.nextDouble();

        if (length <= 0) {
            System.out.println("Invalid length");
            return;
        }

        System.out.println("Enter the breadth of the room(in m)");
        double breadth = scanner.nextDouble();

        if (breadth <= 0) {
            System.out.println("Invalid breadth");
            return;
        }

        System.out.println("Enter the plant area of a single plant(in cm2)");
        double plantArea = scanner.nextDouble();

        if (plantArea <= 0) {
            System.out.println("Invalid plant area");
            return;
        }

        OxygenProduction production = new OxygenProduction(length, breadth, plantArea);
        production.calculate();
    }
}


##height conversion

import java.util.Scanner;

class HeightConverter {
   
    public double convertCmToFeet(double cm) {
        return cm / 30.48;
    }
}

public class UserInterface {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        HeightConverter converter = new HeightConverter();

        System.out.println("Enter height in cm");
        double heightInCm = scanner.nextDouble();

        double heightInFeet = converter.convertCmToFeet(heightInCm);
        System.out.printf("Height in feet is %.2f feet%n", heightInFeet);
        
        scanner.close();
    }
}


##bmi calculator

import java.util.Scanner;

public class UserInterface {
	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);

		System.out.println("Enter weight in kg");
		double weight = scanner.nextDouble();

		System.out.println("Enter height in cm");
		double height = scanner.nextDouble();

		double heightInMeters = height / 100;
		double bmi = weight / (heightInMeters * heightInMeters);

		System.out.printf("Your BMI is %.2f. ", bmi);

		if (bmi >= 25) {
			double kgsToReduce = bmi - 25;
			System.out.printf("You are overweight\n\nReduce %.2f kg to be fit\n", kgsToReduce);
		} else if (bmi < 25 && bmi >= 18.5) {
			System.out.println("You are fit and healthy");
		} else {
			double kgsToGain = 18.5 - bmi;
			System.out.printf("You are underweight\n\nGain %.2f kg to be fit\n", kgsToGain);
		}

		scanner.close();
	}
}


## Sim card

import java.util.Scanner;

public class UserInterface {
	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);

		System.out.println("Enter the phone number");
		long phoneNumber = scanner.nextLong();

		long sumOdd = 0;
		long sumEven = 0;

		long temp = phoneNumber;
		while (temp > 0) {
			long digit = temp % 10;
			if (digit % 2 == 0) {
				sumEven += digit;
			} else {
				sumOdd += digit;
			}
			temp /= 10;
		}

		if (sumOdd > sumEven) {
			System.out.println("Sum of odd is greater than sum of even");
		} else if (sumEven > sumOdd) {
			System.out.println("Sum of even is greater than sum of odd");
		} else {
			System.out.println("Sum of odd and even are equal");
		}

		scanner.close();
	}
}


##Area of the shapes

import java.util.Scanner;

public class UserInterface {
	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);

		System.out.println("Enter the sides");
		int sides = scanner.nextInt();

		double area = 0.0;

		if (sides == 0) {
			System.out.println("Enter the radius");
			double radius = scanner.nextDouble();
			area = 3.14 * radius * radius;
			System.out.printf("Area of the Circle is %.2f\n", area);
		} else if (sides == 3) {
			System.out.println("Enter the base and height");
			double base = scanner.nextDouble();
			double height = scanner.nextDouble();
			area = (base * height) / 2;
			System.out.printf("Area of the Triangle is %.2f\n", area);
		} else if (sides == 4) {
			System.out.println("Enter the length");
			double length = scanner.nextDouble();
			System.out.println("Enter the breadth");
			double breadth = scanner.nextDouble();

			if (length == breadth) {
				area = length * length;
				System.out.printf("Area of the Square is %.2f\n", area);
			} else {
				area = length * breadth;
				System.out.printf("Area of the Rectangle is %.2f\n", area);
			}
		} else {
			System.out.println("Invalid side");
		}

		scanner.close();
	}
}


##Number names

import java.util.Scanner;

public class UserInterface {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter the number");
        String input = scanner.nextLine();
        
        // Array of number names
        String[] numberNames = {
            "zero", "one", "two", "three", "four",
            "five", "six", "seven", "eight", "nine"
        };
        
        StringBuilder result = new StringBuilder();
        
        // Convert each character in the input string to its number name
        for (char digit : input.toCharArray()) {
            if (Character.isDigit(digit)) {
                int num = Character.getNumericValue(digit);
                result.append(numberNames[num]).append(" ");
            }
        }
        
        // Print the result, trimming any trailing space
        System.out.println(result.toString().trim());
        
        scanner.close();
    }
}


##Lottery winner

import java.util.Scanner;

class LotteryTicket {
    private String ticketId;
    private String unluckyCode;

    public LotteryTicket(String ticketId, String unluckyCode) {
        this.ticketId = ticketId;
        this.unluckyCode = unluckyCode;
    }

    public void checkLuckiness() {
        int count = 0;
        for (char ch : ticketId.toCharArray()) {
            if (String.valueOf(ch).equals(unluckyCode)) {
                count++;
            }
        }
        
        if (count == 0) {
            System.out.println(ticketId + " is lucky ticket");
        } else if (count < 3) {
            System.out.println(ticketId + " is partially lucky");
        } else {
            System.out.println(ticketId + " is unlucky ticket");
        }
    }
}

public class UserInterface {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter the ticket Id");
        String ticketId = scanner.nextLine();
        
        System.out.println("Enter the unlucky code");
        String unluckyCode = scanner.nextLine();

        LotteryTicket lotteryTicket = new LotteryTicket(ticketId, unluckyCode);
        lotteryTicket.checkLuckiness();
    }
}


##Ludo king

import java.util.Scanner;

class Player {
	private String name;
	private int points;

	public Player(String name, int points) {
		this.name = name;
		this.points = points;
	}

	public String getName() {
		return name;
	}

	public int getPoints() {
		return points;
	}
}

public class UserInterface {
	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
		Player[] players = new Player[3];
		String[] names = { "Alex", "Nikil", "Sam" };

		for (int i = 0; i < 3; i++) {
			System.out.printf("Enter %s points%n", names[i]);
			int points = scanner.nextInt();

			if (points < 0 || points > 50) {
				System.out.printf("%d is an invalid number%n", points);
				return;
			}
			players[i] = new Player(names[i], points);
		}

		int maxPoints = players[0].getPoints();
		boolean isTie = false;

		for (int i = 1; i < players.length; i++) {
			if (players[i].getPoints() > maxPoints) {
				maxPoints = players[i].getPoints();
				isTie = false;
			} else if (players[i].getPoints() == maxPoints) {
				isTie = true;
			}
		}

		if (isTie) {
			System.out.println("The game is a tie");
		} else {
			for (Player player : players) {
				if (player.getPoints() == maxPoints) {
					System.out.printf("%s scored %d points and won the game%n", player.getName(), player.getPoints());
				}
			}
		}

		scanner.close();
	}
}


##Number play

import java.util.Scanner;

class NumberPuzzle {
	private int number;

	public NumberPuzzle(int number) {
		this.number = number;
	}

	public int calculateDifference() {
		if (number > 50) {
			return (number / 10) - (number % 10);
		} else {
			int reversed = (number % 10) * 10 + (number / 10);
			return (reversed / 10) - (reversed % 10);
		}
	}
}

public class UserInterface {
	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
		System.out.println("Enter the number");
		int input = scanner.nextInt();

		if (input < 10 || input > 99) {
			System.out.println("Invalid number");
		} else {
			NumberPuzzle puzzle = new NumberPuzzle(input);
			System.out.println(puzzle.calculateDifference());
		}
	}
}




