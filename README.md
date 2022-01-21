**# List of .Net programs for 1st semester MSc**<br>
**1.Binary Triangle<br>**
using System;<br>

namespace Exercises<br><br>
{<br>
    class BinaryTriangle<br>
    {<br>
        static void Main(string[] args)<br>
        {<br>
            int number, digit = 1;<br>
            Console.Write("\nEnter the number of lines:");<br>
            number = Convert.ToInt32(Console.ReadLine());<br>
            for (int i = 1; i <= number; i++)<br>
            {<br>
                for (int space = number - i; space > 0; space--)<br>
                {<br>
                    Console.Write(" ");<br>
                }<br>
                for (int j = 0; j < i; j++)<br>
                {<br>
                    Console.Write(digit + " ");<br>
                    digit = (digit == 1) ? 0 : 1;<br>
                }<br>
                Console.Write("\n");<br>

            }
        }
    }
}<br>

output:-
![image](https://user-images.githubusercontent.com/98141711/150476657-3e2d7aa5-0678-4fcb-a6a6-678c2dfb738d.png)
<br>
<br>
<br>
**2.Amicable Number**
using System;

namespace exercises
{
    class AmicableNumber
    {
        static void main(string[] args)
        {
            int num1, num2, sum1 = 0, sum2 = 0;
            Console.WriteLine("\n____AMICABLE NUMBERS____\n");
            Console.Write("\nEnter the first number:");
            num1 = Convert.ToInt32(Console.ReadLine());
            Console.Write("\nEnter the second number:");
            num2 = Convert.ToInt32(Console.ReadLine());
            for (int i = 1; i < num1; i++)
            {
                if (num1 % i == 0)
                {
                    sum1 += i;
                }
            }
            for(int i=1;i<num2;i++)
            {
                if(num2%i==0)
                {
                    sum2 += i;
                }
            }
            if(sum1==num2&&sum2==num1)
            {
                Console.WriteLine("\nThe numbers {0} and {1} are amiciable", num1, num2);
            }
            else
            {
                Console.WriteLine("\nThe numbers {0} and {1} are not amiciable", num1, num2);
            }
        }
    }
}
<br>
output:-![image](https://user-images.githubusercontent.com/98141711/150485652-8feec481-9658-4c4f-90e3-023483d65f92.png)
<br>
<br>![image](https://user-images.githubusercontent.com/98141711/150485816-306b5641-042d-40dc-a0f2-2122667db15a.png)


