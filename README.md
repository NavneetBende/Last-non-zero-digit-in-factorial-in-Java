# Last-non-zero-digit-in-factorial-in-Java

Last non-zero digit in factorial in Java
Here, in this page we will discuss the program to find the Last non-zero digit in factorial in Java programming Language. We will discuss various methods to solve the given problem.

Last non-zero digit in factorial in Java
Method Discussed :
Method 1 : Naive Approach
Method 2 : Efficient Approach
Let’s discuss them one by one in brief,

Method 1:
Run a loop till i<j, inside loop check if (arr[i]==arr[j]), then increase the value of i by 1 and decrease the value of j by 1.
Else if (arr[i]>arr[j]), then set arr[j-1] = arr[j-1]+arr[j] and decrease the value of j and increase the value of count by 1.
Else set, arr[i+1] = arr[i]+arr[i+1] and increase the value of i and count by 1.
After the traversal print the value of count.
Time and Space Complexity :
Time-Complexity : O(n)
Space-Complexity : O(1)
Method 1 : Code in Java
Run
class Main {
 
    // Method to find factorial of the given number
    static int factorial(int n)
    {
        if(n==0 || n==1)
        return 1;
        
        return n*factorial(n-1);
    }
 
    // Driver method
    public static void main(String[] args)
    {
        int num = 5;
        int fact = factorial(num);
        
        int res;
        
        while(fact%10==0){
            fact /=10;
        }
        
        System.out.println(fact%10);
    }
}
Output :
2
Method 2:
Now divide each array element into its shortest divisible form by 2 and decrease count of such occurrences. This way we are not considering the multiplication of 2 and a 5 in our multiplication(number of 2’s present in multiplication result upto n is always more than number 0f 5’s).
Multiply each number(after removing pairs of 2’s and 5’s) now and store just last digit by taking remainder by 10.
Now call recursively for smaller numbers by (currentNumber – 1) as parameter.
Method 2 : Code in Java
Run
import java.io.*;
 
class Main {
   
    public static void callMeFactorialLastDigit(int n, int[] result, int sumOf5)
    {
        int number = n;
        if (number == 1)
            return; 
 
        while (number % 5 == 0) {
            number /= 5;
            sumOf5++;
        }
 
        while (sumOf5 != 0 && (number & 1) == 0) {
            number >>= 1; 
            sumOf5--;
        }
 
        result[0] = (result[0] * (number % 10)) % 10;
        callMeFactorialLastDigit(n - 1, result, sumOf5);
    }
 
    public static int lastNon0Digit(int n)
    {
        int[] result = { 1 }; 
        callMeFactorialLastDigit(n, result, 0);
        return result[0];
    }
 
    public static void main(String[] args)
    {
        System.out.println(lastNon0Digit(7)); 
        
    }
}  
Output :
4
