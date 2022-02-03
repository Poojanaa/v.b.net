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

output:-<br>
![image](https://user-images.githubusercontent.com/98141711/150476657-3e2d7aa5-0678-4fcb-a6a6-678c2dfb738d.png)<br>
<br>
<br>
<br>
**2.Amicable Number**<br>
using System;<br>

namespace exercises<br>
{<br>
    class AmicableNumber<br>
    {<br>
        static void main(string[] args)<br>
        {<br>
            int num1, num2, sum1 = 0, sum2 = 0;<br>
            Console.WriteLine("\n____AMICABLE NUMBERS____\n");<br>
            Console.Write("\nEnter the first number:");<br>
            num1 = Convert.ToInt32(Console.ReadLine());<br>
            Console.Write("\nEnter the second number:");<br>
            num2 = Convert.ToInt32(Console.ReadLine());<br>
            for (int i = 1; i < num1; i++)<br>
            {<br>
                if (num1 % i == 0)<br>
                {<br>
                    sum1 += i;<br>
                }<br>
            }<br>
            for(int i=1;i<num2;i++)<br>
            {<br>
                if(num2%i==0)<br>
                {<br>
                    sum2 += i;<br>
                }<br>
            }<br>
            if(sum1==num2&&sum2==num1)<br>
            {<br>
                Console.WriteLine("\nThe numbers {0} and {1} are amiciable", num1, num2);<br>
            }<br>
            else<br>
            {<br>
                Console.WriteLine("\nThe numbers {0} and {1} are not amiciable", num1, num2);<br>
            }<br>
        }<br>
    }<br>
}<br>
<br>
output:-![image](https://user-images.githubusercontent.com/98141711/150485652-8feec481-9658-4c4f-90e3-023483d65f92.png)<br>
<br><br>
<br>![image](https://user-images.githubusercontent.com/98141711/150485816-306b5641-042d-40dc-a0f2-2122667db15a.png)<br>
<br>
<br>
**3.Multilevel inheritance**<br>
using System;<br>

namespace Exercises<br>
{<br>
    class PersonalDetails<br>
    {<br>
        string name;<br>
        int age;<br>
        string gender;<br>
        public PersonalDetails(string name,int age,string gender)<br>
        {<br>
            this.name = name;<br>
            this.age = age;<br>
            this.gender = gender;<br>
        }<br>
        public virtual void Display()<br>
        {<br>
            Console.WriteLine("\n_____PERSONAL DETAILS_____\n");<br>
            Console.WriteLine("Name :" + name);<br>
            Console.WriteLine("Age :" + age);<br>
            Console.WriteLine("Gender :" + gender);<br>
        }<br>
    }<br>
    class CourseDetails : PersonalDetails<br>
    {<br>
        int regNo;<br>
        string course;<br>
        int semester;<br>
        public CourseDetails(string name, int age, string gender, int regno, string course, int semester) : base(name, age, gender)<br>
        {<br>
            this.regNo = regno;<br>
            this.course = course;<br>
            this.semester = semester;<br>
        }<br>
        public override void Display()<br>
        {<br>
            base.Display();<br>
            Console.WriteLine("Register Number:" + regNo);<br>
            Console.WriteLine("Course :" + course);<br>
            Console.WriteLine("Semester :" + semester);<br>
        }<br>
    }<br>
    class MarksDetails : CourseDetails<br>
    {<br>
        int[] marks = new int[5];<br>
        int total;<br>
        float average;<br>
        string grade;<br>
        int flagFail;<br>
        public MarksDetails(string name,int age,string gender,int regNo,string course,int semester,int[] marks):base(name,age,gender,regNo,course,semester)<br>
        {<br>
            total = 0;<br>
            for(int i=0;i<5;i++)<br>
            {<br>
                this.marks[i] = marks[i];<br>
                total += marks[i];<br>
                if (marks[i]<35)<br>
                {<br>
                    flagFail = 1;<br>
                }<br>
            }<br>
            Calculate();<br>
        }<br>
        private void Calculate()<br>
        {<br>
            average = total / 5;<br>
            if (flagFail == 1 || average < 40)<br>
                grade = "Fail";<br>
            else if (average >= 70)<br>
                grade = "Distinction";<br>
            else if (average >= 60)<br>
                grade = "FirstClass";<br>
            else if (average >= 50)<br>
                grade = "second class";<br>
            else<br>
                grade = "Pass class";<br>
        }<br>
        public override void Display()<br>
        {<br>
            base.Display();<br>
            Console.WriteLine("\n_____MARKS DETAILS_____\n");<br>
            Console.Write("Marks in 5 subjects:");<br>
            for (int i = 0; i < 5; i++)<br>
            Console.Write(marks[i] + " ");<br>
            Console.WriteLine();<br>
            Console.WriteLine("Total :" + total);<br>
            Console.WriteLine("Average :" + average);<br>
            Console.WriteLine("Grade :" + grade);<br>
        }<br>
    }<br>
    class Multilevel<br>
    {<br>
        public static void Main(string[] args)<br>
        {<br>
            MarksDetails Student1 = new MarksDetails("Abhijith", 22, "Male", 20190001, "MCA", 5, new int[] { 77, 80, 98, 95, 90 });<br>
            Student1.Display();<br>
        }<br>
    }<br>
}<br>
**Output:-**<br>

_____PERSONAL DETAILS_____<br>

Name :Abhijith<br>
Age :22<br>
Gender :Male<br>
Register Number:20190001<br>
Course :MCA<br>
Semester :5<br>

_____MARKS DETAILS_____<br>

Marks in 5 subjects:77 80 98 95 90<br>
Total :440<br>
Average :88<br>
Grade :Distinction<br>
<br>
<br>
**4.Gray code**<br>
using System;<br>

namespace Exercises<br>
{<br>
    class GrayCode<br>
    {<br>
        static int getGray(int n)<br>
        {<br>
            return n ^ (n >> 1);<br>
        }<br>
        static void Main(string[] args)<br>
        {<br>
            int InputNum, GrayNum;<br>
            Console.Write("\nEnter the decimal number:");<br>
            InputNum = Convert.ToInt32(Console.ReadLine());<br>
            Console.WriteLine("\n Binary equivalent of {0} : {1}", InputNum, Convert.ToString(InputNum, 2));<br>
            GrayNum = getGray(InputNum);<br>
            Console.WriteLine("\nGrey Code equivalent of {0} :{1}", InputNum, Convert.ToString(GrayNum, 2));<br>
        }<br>
    }<br>
}<br>

**Output:-**<br>

Enter the decimal number:123<br>

 Binary equivalent of 123 : 1111011<br>

Grey Code equivalent of 123 :1000110<br>
<br>
<br>
**5.Volume of 2 boxes**<br>
using System;<br>

namespace eXERCISES<br>
{<br>
    class BOX<br>
    {<br>
        float width;<br>
        float height;<br>
        float length;<br>
        public float Volume<br>
        {<br>
            get { return width * height * length; }<br>
        }<br>
        public BOX(float width, float height, float length)<br>
        {<br>
            this.width = width;<br>
            this.height = height;<br>
            this.length = length;<br>
        }<br>
        public static float operator +(BOX box1, BOX box2)<br>
        {<br>
            return box1.Volume + box2.Volume;<br>
        }<br>
        public override string ToString()<br>
        {<br>
            return "box with width" + width + ",height" + height + "and length" + length;<br>
        }<br>
    }<br>
    class OperatorOverloading<br>
    {<br>
        public static void Main()<br>
        {<br>
        BOX box1 = new BOX(10, 20, 30);<br>
        BOX box2 = new BOX(25, 32, 15);<br>
        Console.WriteLine("Volume of {0} is : {1}",box1,box1.Volume);<br>
        Console.WriteLine("Volume of {0} is : {1}",box2,box2.Volume);<br>
        Console.WriteLine("Volume after adding boxes : {0}",box1 + box2);<br>
        }<br>
    }<br>
}<br>
<br>
**Output:-**<br>
Volume of box with width10,height20and length30 is : 6000<br>
Volume of box with width25,height32and length15 is : 12000<br>
Volume after adding boxes : 18000<br>
<br>                                  
<br>                               
<br>
**6.Delegates string program**<br>
using System;<br>

namespace Exercises<br>
{<br>
    class Delegates<br>
    {<br>
        delegate string UppercaseDelegate(string input);<br>
        static string UppercaseFirst(string input)<br>
        {<br>
            char[] buffer = input.ToCharArray();<br>
            buffer[0] = char.ToUpper(buffer[0]);<br>
            return new string(buffer);<br>
        }<br>
        static string UppercaseLast(string input)<br>
        {<br>
            char[] buffer = input.ToCharArray();<br>
            buffer[buffer.Length - 1] = char.ToUpper(buffer[buffer.Length - 1]);<br>
            return new string(buffer);<br>
        }<br>
        static string UppercaseAll(string input)<br>
        {<br>
            return input.ToUpper();<br>

        }<br>
        static void WriteOutput(string input,UppercaseDelegate del)<br>
        {<br>
            Console.WriteLine("Input String : {0}", input);<br>
            Console.WriteLine("Output String : {0}", del(input));<br>
        }<br>
        static void Main()<br>
        {<br>
            WriteOutput("tom", new UppercaseDelegate(UppercaseFirst));<br>
            WriteOutput("tom", new UppercaseDelegate(UppercaseLast));<br>
            WriteOutput("tom", new UppercaseDelegate(UppercaseAll));<br>
            Console.ReadLine();<br>
        }<br>
    }<br>
}<br>
<br>
**Output:-**<br>
Input String : tom<br>
Output String : Tom<br>
Input String : tom<br>
Output String : toM<br>
Input String : tom<br>
Output String : TOM<br>
<br>
<br>
**7.100 students register number using static constructor**<br>




