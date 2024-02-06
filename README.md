public class Calculator{

    double add(double num1, double num2){
        double sum=num1+num2;
        System.out.println(sum);
        return sum;
    }
    double subtract(double num1,double num2){
        double difference=num1-num2;
        System.out.println(difference);
        return difference;
    }
    double multiply(double num1, double num2){
        double product=num1*num2;
        System.out.println(product);
        return product;
    }
    double divide(double num1, double num2){
        double quotient=num1/num2;
        System.out.println(quotient);
        return quotient;
    }

    double squareRoot(double num1){
        double sqRt=sqrt(num1);
        System.out.println(sqRt);
        return sqRt;
    }

    double power(double num1, double num2){
        double Power=pow(num1,num2);
        System.out.println(Power);
        return Power;

    }
    double mean(){
        Scanner sc = new Scanner(System.in);
        double sum=0;
        double average;
        int count=0;
        System.out.println("Enter numbers for average calculation (type 'end' to finish): ");
        while (sc.hasNext()) {
            if (sc.hasNextDouble()) {
                double number = sc.nextDouble();
                sum += number;
                count=count+1;
            } else {
                String input = sc.next();
                if (input.equals("end")) {
                    break;
                } else {
                    System.out.println("Invalid input. Please enter a number or 'end'.");
                }
            }
        }
        average=sum/count;
        if (count > 0) {
            System.out.println("Average of numbers: " + average);
            return average;
        }
        else {
            System.out.println("No numbers entered.");
        }
    return average;
    }

    double variance(){
        double dev,sqDev,sum_sqDev=0,average,Variance=0;
        int count=0;

        Calculator calculator=new Calculator();
        Scanner sc = new Scanner(System.in);
        System.out.println("Step 1: Calculating the mean of the numbers for variance calculation.");
        System.out.println(calculator.mean());
        average=calculator.mean();


        while (sc.hasNext()) {
            if (sc.hasNextDouble()) {
                double number = sc.nextDouble();
                dev = number-average;
                sqDev=dev*dev;
                sum_sqDev+=sqDev;
                count++;
            }
            else {
                String input = sc.next();
                if (input.equals("end")) {
                    break;
                }
                else {
                    System.out.println("Invalid input. Please enter a number or 'end'.");
                }
            }
        }

        if (count > 0) {
            Variance= Variance+ sum_sqDev /count;
            System.out.println("Variance of numbers: " + Variance);

        }
        else {
            System.out.println("No numbers entered.");
        }
        return Variance;
    }

}

public class Operations extends Calculator {
    Input in = new Input();

    public static void main(String[] args) {
        // TODO Auto-generated method stub
        Scanner sc = new Scanner(System.in);
        double no[] = new double[2];
        System.out.println("Enter 2 Numbers");
        no[0] = sc.nextDouble();
        no[1] = sc.nextDouble();

        double[] NumsOps;
        Calculator calc = new Calculator();
        //Scanner sc = new Scanner(System.in);
        int option = 0;
        System.out.println("------------- Operations-----");
        System.out.println("1. Addition");
        System.out.println("2. Subtraction");
        System.out.println("3. Mean");
        System.out.println("4. Variance");
        System.out.println("5. Multiplication");
        System.out.println("6. Division");
        System.out.println("7. Power");
        System.out.println("8. Square Root");
        System.out.println("Enter option (1 to 8) for operation");
        option = sc.nextInt();

        switch (option) {
            case 1:
                System.out.println("Addition is " +
                        calc.add(no[0], no[1]));
                break;
            case 2:
                System.out.println("Subtraction is " +
                        calc.subtract(no[0], no[1]));
                break;

            case 3:
                System.out.println("Mean is " + calc.mean());
                break;

            case 4:
                System.out.println("Variance is " + calc.variance());
                break;
            case 5:
                System.out.println("Multiplication is " + calc.multiply(no[0], no[1]));
                break;

            case 6:
                System.out.println("Division is " + calc.divide(no[0], no[1]));
                break;

            case 7:
                System.out.println("Exponent is " + calc.power(no[0], no[1]));
                break;

            case 8:
                System.out.println("Square Root is " + calc.squareRoot(no[0]));

        }


    }
    
 public class InputMethods {
    public static long calculateFactorial(int n) {
        if (n < 0) {
            throw new IllegalArgumentException("Factorial is not defined for negative numbers");
        }
        long factorial = 1;
        for (int i = 1; i <= n; i++) {
            factorial *= i;
        }
        return factorial;
    }
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        DataInputStream dataInputStream = new DataInputStream(System.in);

        while (true) {
            System.out.println("Choose an input method:");
            System.out.println("1. Command Line Arguments");
            System.out.println("2. Scanner");
            System.out.println("3. BufferedReader");
            System.out.println("4. DataInputStream");
            System.out.println("5. Console");
            System.out.println("6. Exit");
            System.out.print("Enter your choice: ");

            int choice;
            try {
                choice = Integer.parseInt(reader.readLine());
            } catch (NumberFormatException e) {
                System.out.println("Invalid choice. Please enter a number.");
                continue;
            }

            switch (choice) {
                case 1:
                    commandLineArgs(args);
                    break;
                case 2:
                    scannerInput();
                    break;
                case 3:
                    bufferedReaderInput();
                    break;
                case 4:
                    dataInputStreamInput();
                    break;
                case 5:
                    consoleInput();
                    break;
                case 6:
                    System.out.println("Exiting program...");
                    return;
                default:
                    System.out.println("Invalid choice. Please enter a number between 1 and 6.");
            }
        }
    }

    private static void commandLineArgs(String[] args) {
        System.out.println("Command Line Arguments:");
        if (args.length != 1) {
            System.out.println("Usage: java FactorialCalculator <number>");
            System.exit(1);
        }

        int number = Integer.parseInt(args[0]);

        long factorial = calculateFactorial(number);

        System.out.println("The factorial of " + number + " is: " + factorial);
    }

    private static void scannerInput() {
        // You can implement Scanner input here
        System.out.println("Scanner input method");
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a number to compute its factorial: ");
        int number = scanner.nextInt();

        long factorial = calculateFactorial(number);

        System.out.println("The factorial of " + number + " is: " + factorial);

        scanner.close();
    }

    private static void bufferedReaderInput() throws IOException {
        System.out.println("BufferedReader input method");
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        System.out.print("Enter a number to compute its factorial: ");
        int number = Integer.parseInt(reader.readLine());
        long factorial = calculateFactorial(number);
        System.out.println("The factorial of " + number + " is: " + factorial);
        reader.close();

    }

    private static void dataInputStreamInput() throws IOException {
        System.out.println("DataInputStream input method");
        DataInputStream dis = new DataInputStream(System.in);

        try {
            System.out.print("Enter a number to compute its factorial: ");
            int number = Integer.parseInt(dis.readLine());

            long factorial = calculateFactorial(number);

            System.out.println("The factorial of " + number + " is: " + factorial);
        } catch (IOException | NumberFormatException e) {
            System.out.println("Invalid input. Please enter a valid integer.");
            e.printStackTrace();
        } finally {
            try {
                dis.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }

    private static void consoleInput() throws IOException{
        // You can implement Console input here
        System.out.println("Console input method");
        Console console = System.console();
        if (console == null) {
            System.out.println("Console is not available");
            System.exit(1);
        }

        String inputString = console.readLine("Enter a number to compute its factorial: ");
        int number = Integer.parseInt(inputString);

        long factorial = calculateFactorial(number);

        console.printf("The factorial of %d is: %d%n", number, factorial);
    }

}


}
