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
