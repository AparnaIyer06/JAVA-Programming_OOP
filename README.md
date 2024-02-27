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

import java.util.Scanner;
import java.util.ArrayList;
import java.util.Arrays;
public class Input {
    public int[] inputData() {

        Scanner sc = new Scanner(System.in); //Initialize Scanner Object
        System.out.println("Enter size of an Array:");
        int size = sc.nextInt(); //Size of the array taken from the user
        int data[] = new int[size]; //Array is of this size
        System.out.println("Enter data: ");
        for (int i = 0; i < size; i++)
            data[i] = sc.nextInt();
        return data;
    }
}

public class Assignment2 extends Input{
    //Part 1: WAP that declares two arrays named even and odd. Accept numbers from the user.
    // Move them to respective arrays depending on whether they are even or odd.

    public void part1() {
        Input input = new Input();
        int data[] = new int[10];
        data = input.inputData();
        int len = data.length;
        int[] evenArray = new int[len];
        int[] oddArray = new int[len];
        int evenCnt = 0, oddCnt = 0;
        for (int i = 0; i < len; i++) {
            if (data[i] % 2 == 0) {
                evenArray[evenCnt] = data[i];
                evenCnt++;
            } else {
                oddArray[oddCnt] = data[i];
                oddCnt++;
            }//else
        }//for
        System.out.println("Original Array");
        for (int i = 0; i < data.length; i++)
            System.out.println(data[i] + "\t");
        System.out.println("Even Array");
        for (int i = 0; i < evenCnt; i++)
            System.out.println(evenArray[i] + "\t");
        System.out.println("Odd Array");
        for (int i = 0; i < oddCnt; i++)
            System.out.println(oddArray[i] + "\t");
    }//part1

    //Part 2: Implement a JAVA Method that finds two neighbouring numbers in an array with the smallest distance to each.
    // It should return the index of the 1st no.
    public void part2() {
        Input input = new Input();
        int data[] = new int[10];
        data = input.inputData();
        int len = data.length;
        int[] diff = new int[len]; //An array to store the differences between successive terms
        for (int i = 0; i < len; i++) {
            diff[i] = data[i + 1] - data[i]; //Create array diff
        }//for
        //Find the first smallest value in the array diff
        int minVal; //Initialize a variable that stores the minimum difference.
        for (int i = 0; i < len; i++) {
            if (diff[i] > diff[i + 1])
                minVal = diff[i + 1];
            else
                minVal = diff[i];
        }
        //Iterate through array diff to find the index of the minVal
        for (int i = 0; i < len; i++) {
            if (diff[i] == minVal) {
                System.out.println("Index of first number for minimum difference: " + i);
                System.out.println("Element at position" + i + data[i]); //Returns the element in the original array that is at the first position with min. difference
            }
        }
    }

    //Part 3: WAP to convert an array to an ArrayList and vice-versa.
    public void part3()
    {
        //a. Convert an array into an ArrayList.
        Scanner sc = new Scanner(System.in);
        // Prompt the user to enter the number of elements
        System.out.print("Enter the number of elements: ");
        int numElements = sc.nextInt();

        // Create the array to store the elements
        int[] data = new int[numElements];
        // Prompt the user to enter elements
        System.out.println("Enter the elements:");
        //Add elements to the array created
        for (int i = 0; i < numElements; i++) {
            System.out.print("Element " + (i + 1) + ": ");
            data[i] = sc.nextInt();
        }

        // Convert array to ArrayList
        ArrayList<String> arrayList = new ArrayList<>();
        arrayList=Arrays.asList(data);

        // Display the elements of the ArrayList
        System.out.println("Elements of the ArrayList:");
        for (String element : arrayList) {
            System.out.println(element);
        }

        // b. Convert an ArrayList into an array
        Scanner sc = new Scanner(System.in);
        // Create an ArrayList
        ArrayList<String> al = new ArrayList<>();
        int aLSize=arrayList.size();
        // Add elements to the ArrayList
        for(int i=1;i<aLSize+1;i++){
            System.out.println("Enter ArrayList element "+i+":");
            String element=sc.next();
            al.add(element);
        }
        System.out.println("The original arraylist is "+al);
        // Convert ArrayList to Array
        String[] array = new String[arrayList.size()];
        al.toArray(array);

        // Display the elements of the array
        System.out.println("Elements of the array:");
        for (String element : array) {
            System.out.println(element);
    }
    }


}

public class Main{
    public static void main(String[] args)
    {
        Assignment2 assignment2=new Assignment2;
        assignment2.part1();
        assignment2.part2();
        assignment2.part3();
    }
}

_______________

import java.util.Scanner;

public abstract class Employee {
    Scanner sc=new Scanner(System.in);
    private String empName,empAddress,empDesignation,empDept,doj,bankName;
    private long UAN,PF_NO,ESINo,empId,bankAcctNo;
    private int totalWorkingDays,paidDays,leavesTaken,lopDays;
    private double grosswage,totalEarning,totalDeductions,basicWage,hra,conveyanceAllowances,
            medicalAllowances,otherAllowances,epf,esi,pt,loanRecovery,netSalary;

    public String getEmpName() {
        return empName;
    }

    public void setEmpName(String empName) {
        this.empName = empName;
    }

    public double getNetSalary(){
        return netSalary;
    }

    public void setNetSalary(double netSalary){
        this.netSalary=netSalary;
    }
    public String getEmpAddress() {
        return empAddress;
    }

    public void setEmpAddress(String empAddress) {
        this.empAddress = empAddress;
    }

    public String getEmpDesignation() {
        return empDesignation;
    }

    public void setEmpDesignation(String empDesignation) {
        this.empDesignation = empDesignation;
    }

    public String getEmpDept() {
        return empDept;
    }

    public void setEmpDept(String empDept) {
        this.empDept = empDept;
    }

    public String getDoj() {
        return doj;
    }

    public void setDoj(String doj) {
        this.doj = doj;
    }

    public String getBankName() {
        return bankName;
    }

    public void setBankName(String bankName) {
        this.bankName = bankName;
    }

    public long getUAN() {
        return UAN;
    }

    public void setUAN(long UAN) {
        this.UAN = UAN;
    }

    public long getPF_NO() {
        return PF_NO;
    }

    public void setPF_NO(long PF_NO) {
        this.PF_NO = PF_NO;
    }

    public long getESINo() {
        return ESINo;
    }

    public void setESINo(long ESINo) {
        this.ESINo = ESINo;
    }

    public long getEmpId() {
        return empId;
    }

    public void setEmpId(long empId) {
        this.empId = empId;
    }

    public long getBankAcctNo() {
        return bankAcctNo;
    }

    public void setBankAcctNo(long bankAcctNo) {
        this.bankAcctNo = bankAcctNo;
    }

    public int getTotalWorkingDays() {
        return totalWorkingDays;
    }

    public void setTotalWorkingDays(int totalWorkingDays) {
        this.totalWorkingDays = totalWorkingDays;
    }

    public int getPaidDays() {
        return paidDays;
    }

    public void setPaidDays(int paidDays) {
        this.paidDays = paidDays;
    }

    public int getLeavesTaken() {
        return leavesTaken;
    }

    public void setLeavesTaken(int leavesTaken) {
        this.leavesTaken = leavesTaken;
    }

    public int getLopDays() {
        return lopDays;
    }

    public void setLopDays(int lopDays) {
        this.lopDays = lopDays;
    }

    public double getGrosswage() {
        return grosswage;
    }

    public void setGrosswage(double grosswage) {
        this.grosswage = grosswage;
    }

    public double getTotalEarning() {
        return totalEarning;
    }

    public void setTotalEarning(double totalEarning) {
        this.totalEarning = totalEarning;
    }

    public double getTotalDeductions() {
        return totalDeductions;
    }

    public void setTotalDeductions(double totalDeductions) {
        this.totalDeductions = totalDeductions;
    }

    public double getBasicWage() {
        return basicWage;
    }

    public void setBasicWage(double basicWage) {
        this.basicWage = basicWage;
    }

    public double getHra() {
        return hra;
    }

    public void setHra(double hra) {
        this.hra = hra;
    }

    public double getConveyanceAllowances() {
        return conveyanceAllowances;
    }

    public void setConveyanceAllowances(double conveyanceAllowances) {
        this.conveyanceAllowances = conveyanceAllowances;
    }

    public double getMedicalAllowances() {
        return medicalAllowances;
    }

    public void setMedicalAllowances(double medicalAllowances) {
        this.medicalAllowances = medicalAllowances;
    }

    public double getOtherAllowances() {
        return otherAllowances;
    }

    public void setOtherAllowances(double otherAllowances) {
        this.otherAllowances = otherAllowances;
    }

    public double getEpf() {
        return epf;
    }

    public void setEpf(double epf) {
        this.epf = epf;
    }

    public double getEsi() {
        return esi;
    }

    public void setEsi(double esi) {
        this.esi = esi;
    }

    public double getPt() {
        return pt;
    }

    public void setPt(double pt) {
        this.pt = pt;
    }

    public double getLoanRecovery() {
        return loanRecovery;
    }

    public void setLoanRecovery(double loanRecovery) {
        this.loanRecovery = loanRecovery;
    }
    public abstract void salaryCalculation();
    public abstract void deductionCalculation();
    public abstract void netsalaryCalculation();

    public void getEmployeeDetails()
    {
        System.out.println("Employee Id");
        long eid=sc.nextLong();
        setEmpId(eid);
        System.out.println("Employee Name");
        String ename=sc.next();
        setEmpName(ename);
        System.out.println("Employee Designation");
        String d = sc.next();
        setEmpDesignation(d);
        System.out.println("Employee Department");
        String dept=sc.next();
        setEmpDept(dept);
        System.out.println("Employee DOJ");
        String doj=sc.next();
        setDoj(doj);
        System.out.println("Employee UAN");
        long u=sc.nextLong();
        setUAN(u);
        System.out.println("Employee PF Number");
        long pf=sc.nextLong();
        setPF_NO(pf);
        System.out.println("Employee ESI Number");
        long esi=sc.nextLong();
        setEsi(esi);
        System.out.println("Employee Bank Name");
        String bn=sc.next();
        setBankName(bn);
        System.out.println("Employee Bank Account No");
        long acct=sc.nextLong();
        setBankAcctNo(acct);
        System.out.println("Employee Gross Wage");
        double gw=sc.nextDouble();
        setGrosswage(gw);
        setTotalWorkingDays(30);
        setLopDays(1);
        setPaidDays(getTotalWorkingDays()-getLopDays());
        System.out.println("Employee leaves taken");
        int lt=sc.nextInt();
        setLeavesTaken(lt);
    }
}

package assignment_5;

public class NormalEmployee extends assignment_5.Employee {
    @Override
    public void salaryCalculation() {
        System.out.println("Earnings ");
        double bw=((getGrosswage()/getTotalWorkingDays())*getPaidDays())*0.45;
        setBasicWage(bw);
        System.out.println("Basic Wage "+bw);
        double hra=(bw*0.40);
        setHra(hra);
        System.out.println("HRA "+hra);
        double ca=(1600/getTotalWorkingDays())*getPaidDays();
        setConveyanceAllowances(ca);
        System.out.println("Conveyance Allowances "+ca);
        double ma=(1250/getTotalWorkingDays())*getPaidDays();
        setMedicalAllowances(ma);
        System.out.println("Medical Allowances "+ma);
        double otherAllo=((getGrosswage()/getTotalWorkingDays())*getPaidDays())-(bw+hra+ca+ma);
        System.out.println("Other Allowances "+otherAllo);
        setTotalEarning(bw+hra+ca+ma+otherAllo);
        System.out.println("Total Earnings   "+getTotalEarning()+"\n" );
        // return 0;
    }
    @Override
    public void deductionCalculation(){
        System.out.println("Deductions ");
        double epf=(getGrosswage()*0.12+getGrosswage()*0.0367)*(8.15/1200);
        setEpf(epf);
        System.out.println("EPF "+getEpf());
        double esi=(getGrosswage()*(0.75+3.25)*0.01);
        setEsi(esi);
        System.out.println("ESI "+getEsi());
        double pt=(getGrosswage()*0.1);
        setPt(pt);
        System.out.println("Professional Tax "+getPt());
        double loan_rec=0;
        setLoanRecovery(loan_rec);
        System.out.println("Loan Recovery "+getLoanRecovery());
        double total_deductions=epf+esi+pt+loan_rec;
        setTotalDeductions(total_deductions);
        System.out.println("Total Deductions "+getTotalDeductions()+"\n");
    }
    @Override
    public void netsalaryCalculation(){
        double netSalary=getTotalEarning()-getTotalDeductions();
        setNetSalary(netSalary);
        System.out.println("Net Salary: "+getNetSalary());
    }
}

package assignment_5;

public class Main {
    public static void main(String[] args) {
        // System.out.println();
        assignment_5.NormalEmployee n = new assignment_5.NormalEmployee();
        n.getEmployeeDetails();
        n.salaryCalculation();
        n.deductionCalculation();
        n.netsalaryCalculation();
    }
}

