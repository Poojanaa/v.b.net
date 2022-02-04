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
using System;<br>
namespace exercises<br>
{<br>
    class RegisterNum<br>
    {<br>
        int regNo;<br>
        static int startNum;<br>
        static RegisterNum()<br>
        {<br>
            startNum = 20210000;<br>
        }<br>
        RegisterNum()<br>
        {<br>
            regNo = ++startNum;<br>

        }<br>
        public static void Main(string[]args)<br>
        {<br>
            for(int i=0;i<100;i++)<br>
            {<br>
                RegisterNum Student = new RegisterNum();<br>
                Console.WriteLine("Student  {0} : {1}",i + 1, Student.regNo);<br>
            }<br>
        }<br>

    }<br>
}<br>
<br>
<br>
**Output:-**<br>
Student  1 : 20210001<br>
Student  2 : 20210002<br>
Student  3 : 20210003<br>
Student  4 : 20210004<br>
Student  5 : 20210005<br>
Student  6 : 20210006<br>
Student  7 : 20210007<br>
Student  8 : 20210008<br>
Student  9 : 20210009<br>
Student  10 : 20210010<br>
Student  11 : 20210011<br>
Student  12 : 20210012<br>
Student  13 : 20210013<br>
Student  14 : 20210014<br>
Student  15 : 20210015<br>
Student  16 : 20210016<br>
Student  17 : 20210017<br>
Student  18 : 20210018<br>
Student  19 : 20210019<br>
Student  20 : 20210020<br>
Student  21 : 20210021<br>
Student  22 : 20210022<br>
Student  23 : 20210023<br>
Student  24 : 20210024<br>
Student  25 : 20210025<br>
Student  26 : 20210026<br>
Student  27 : 20210027<br>
Student  28 : 20210028<br>
Student  29 : 20210029<br>
Student  30 : 20210030<br>
Student  31 : 20210031<br>
Student  32 : 20210032<br>
Student  33 : 20210033<br>
Student  34 : 20210034<br>
Student  35 : 20210035<br>
Student  36 : 20210036<br>
Student  37 : 20210037<br>
Student  38 : 20210038<br>
Student  39 : 20210039<br>
Student  40 : 20210040<br>
Student  41 : 20210041<br>
Student  42 : 20210042<br>
Student  43 : 20210043<br>
Student  44 : 20210044<br>
Student  45 : 20210045<br>
Student  46 : 20210046<br>
Student  47 : 20210047<br>
Student  48 : 20210048<br>
Student  49 : 20210049<br>
Student  50 : 20210050<br>
Student  51 : 20210051<br>
Student  52 : 20210052<br>
Student  53 : 20210053<br>
Student  54 : 20210054<br>
Student  55 : 20210055<br>
Student  56 : 20210056<br>
Student  57 : 20210057<br>
Student  58 : 20210058<br>
Student  59 : 20210059<br>
Student  60 : 20210060<br>
Student  61 : 20210061<br>
Student  62 : 20210062<br>
Student  63 : 20210063<br>
Student  64 : 20210064<br>
Student  65 : 20210065<br>
Student  66 : 20210066<br>
Student  67 : 20210067<br>
Student  68 : 20210068<br>
Student  69 : 20210069<br>
Student  70 : 20210070<br>
Student  71 : 20210071<br>
Student  72 : 20210072<br>
Student  73 : 20210073<br>
Student  74 : 20210074<br>
Student  75 : 20210075<br>
Student  76 : 20210076<br>
Student  77 : 20210077<br>
Student  78 : 20210078<br>
Student  79 : 20210079<br>
Student  80 : 20210080<br>
Student  81 : 20210081<br>
Student  82 : 20210082<br>
Student  83 : 20210083<br>
Student  84 : 20210084<br>
Student  85 : 20210085<br>
Student  86 : 20210086<br>
Student  87 : 20210087<br>
Student  88 : 20210088<br>
Student  89 : 20210089<br>
Student  90 : 20210090<br>
Student  91 : 20210091<br>
Student  92 : 20210092<br>
Student  93 : 20210093<br>
Student  94 : 20210094<br>
Student  95 : 20210095<br>
Student  96 : 20210096<br>
Student  97 : 20210097<br>
Student  98 : 20210098<br>
Student  99 : 20210099<br>
Student  100 : 20210100<br>
<br>
<br>
<br>
**8.Program to find the frequence of the word "is" in a given sentence**<br>
using System;<br>

namespace Exercises<br>
{<br>
    class FrequencyIS<br>
    {<br>
        static void Main(string[]args)<br>
        {<br>
            int count = 0;<br>
            string inputString;<br>
            Console.WriteLine("\n_____Frequency of word 'is'_____");<br>
            Console.Write("\nEnter the input string:");<br>
            inputString = Console.ReadLine();<br>
            char[] separator = { ',', ' ', '.', '!', '\n' };<br>
            string testString = inputString.ToLower();<br>
            String[] outcomes = testString.Split(separator);<br>
            foreach(String s in outcomes)<br>
            {<br>
                Console.WriteLine(s);<br>
                if(s=="is")<br>
                    count++;<br>
            }<br>
            Console.WriteLine("\n Number of 'is' in '" + inputString + "'is: "+ count);<br>
        }<br>
    }<br>
}<br>
<br>
**Output:-**<br>
____Frequency of word 'is'_____<br>

Enter the input string:This statement is to check frequency of word is<br>
this<br>
statement<br>
is<br>
to<br>
check<br>
frequency<br>
of<br>
word<br>
is<br>

 Number of 'is' in 'This statement is to check frequency of word is'is: 2<br>
<br>

**9.program that benchmarks 2D,jagged array allocation**<br>
using System;<br>
using System.Diagnostics;<br>
namespace Exercises<br>
{<br>
    class BenchmarkAllocation<br>
    {<br>
        const int _max = 100000;<br>
        static void Main(string[]args)<br>
        {<br>
            var Arr2D = new int[100, 100];<br>
            var ArrJagged = new int[100][];<br>
            for(int i=0;i<100;i++)<br>
            {<br>
                ArrJagged[i] = new int[100];<br>
            }<br>
            var Stopwatch2D = Stopwatch.StartNew();<br>
            for(int i=0;i<_max;i++)<br>
            {<br>
                for(int j=0;j<100;j++)<br>
                {<br>
                    for(int k=0;k<100;k++)<br>
                    {<br>
                        Arr2D[j, k] = k;<br>
                    }<br>
                }<br>
            }<br>
            Stopwatch2D.Stop();<br>
            var StopwatchJagged = Stopwatch.StartNew();<br>
            for(int i=0;i<_max;i++)<br>
            {<br>
                for(int j=0;j<100;j++)<br>
                {<br>
                    for(int k=0;k<100;k++)<br>
                    {<br>
                        ArrJagged[j][k] = k;<br>
                    }<br>
                }<br>
            }<br>
            StopwatchJagged.Stop();<br>
            Console.Write("\n Time taken for allocation in case of 2D array:");<br>
            Console.WriteLine(Stopwatch2D.Elapsed.TotalMilliseconds + "milliseconds");<br>
            Console.Write("\n Time taken for allocation in case of Jagged array:");<br>
            Console.WriteLine(StopwatchJagged.Elapsed.TotalMilliseconds + "milliseconds");<br>
        }<br>
    }<br>
}<br>
<br>
<br>
**Output:-**<br>

 Time taken for allocation in case of 2D array:3633.5275milliseconds<br>

 Time taken for allocation in case of Jagged array:2700.978milliseconds<br>
 <br>
 <br>
 **10.Program to find the sum of the value on diagonal of the matrix**<br>
 using System;<br>

namespace Exercises<br>
{<br>
    class SumOfDiagonals<br>
    {<br>
        static void Main(string[]args)<br>
        {<br>
            int MaxRow, MaxCol, Sum = 0;<br>
            int[,] Matrix;<br>
            Console.WriteLine("\n_____SUM OF DIAGONAL OF A MATRIX_____\n");<br>
            Console.Write("\n Enter the number of rows:");<br>
            MaxRow = Convert.ToInt32(Console.ReadLine());<br>
            Console.Write("\n Enter the number of columns:");<br>
            MaxCol = Convert.ToInt32(Console.ReadLine());<br>
            if(MaxRow!=MaxCol)<br>
            {<br>
                Console.WriteLine("\n the Dimensions enterd are not of Square Matrix.");<br>
                Console.WriteLine("\n Exiting the Program..");<br>
                return;<br>
            }<br>
            Matrix = new int[MaxRow, MaxCol];<br>
            for(int i=0;i<MaxRow;i++)<br>
            {<br>
                for(int j=0;j<MaxCol;j++)<br>
                {<br>
                    Console.Write("\n Enter the ({0},{1})th elsement of the matrix:", (i + 1), (j + 1));<br>
                    Matrix[i, j] = Convert.ToInt32(Console.ReadLine());<br>
                }<br>
            }<br>
            Console.WriteLine("\n the entered Matrix is:");<br>
            for(int i=0;i<MaxRow;i++)<br>
            {<br>
                for(int j=0;j<MaxCol;j++)<br>
                {<br>
                    Console.Write(" " + Matrix[i, j]);<br>
                    if(i==j)<br>
                    {<br>
                        Sum += Matrix[i, j];<br>
                    }<br>
                }<br>
                Console.WriteLine();<br>
            }<br>
            Console.WriteLine("\nThe Sum of Diagonal is" + Sum);<br>
        }<br>
    }<br>
}<br>
<br>
<br>
**Output:-**<br>

_____SUM OF DIAGONAL OF A MATRIX_____<br>


 Enter the number of rows:3<br>

 Enter the number of columns:3<br>

 Enter the (1,1)th elsement of the matrix:1<br>

 Enter the (1,2)th elsement of the matrix:2<br>

 Enter the (1,3)th elsement of the matrix:3<br>

 Enter the (2,1)th elsement of the matrix:4<br>

 Enter the (2,2)th elsement of the matrix:5<br>

 Enter the (2,3)th elsement of the matrix:6<br>

 Enter the (3,1)th elsement of the matrix:7<br>

 Enter the (3,2)th elsement of the matrix:8<br>

 Enter the (3,3)th elsement of the matrix:9<br>

 the entered Matrix is:<br>
 1 2 3<br>
 4 5 6<br>
 7 8 9<br>

The Sum of Diagonal is 15<br>
 <br>
<br>
**11.Program to create ,check and read the content of file**<br>
using System;
using System.IO;
namespace eXERCISES
{
    class FileRead
    {
        public static void Main()
        {
            string fileName;
            while(true)
            {
                Console.WriteLine("\n_____MENU_____\n");
                Console.WriteLine("\n1.Create a File");
                Console.WriteLine("\n2.Existance of the File");
                Console.WriteLine("\n3.Read the contents of the File");
                Console.WriteLine("\n4.Exit");
                Console.Write("\n Enter your choice:");
                int ch = int.Parse(console.Readline());
                switch(ch)
                { 
                    case1:
                        Console.Write("\n Enter the file name to create:");
                        fileName = Console.ReadLine();
                        Console.WriteLine("\n Write the Contents to the File:\n");
                        string r = Console.ReadLine();
                        using(StreamWriter fileStr=File.CreateText(fileName))
                        {
                            fileStr.WriteLine(r);
                        }
                        Console.WriteLine("File is Created...");
                        break;
                    case2:
                        Console.Write("\n Enter the file name:");
                        fileName = Console.ReadLine();
                        if(File.Exists(fileName))
                        {
                            Console.WriteLine("File exists...");
                        }
                        else
                        {
                            Console.WriteLine("File does not exist in the current directory!");
                        }
                        break;
                    case3:
                        Console.Write("Enter the file name to read the contents:\n");
                        fileName = Console.ReadLine();
                        if(File.Exists(fileName))
                        {
                            using (StreamReader sr=File.OpenText(fileName))
                            {
                                string s = "";
                                Console.WriteLine("Here is the content of the file:");
                                while((s=sr.ReadLine())!=null)
                                {
                                    Console.WriteLine(s);
                                }
                                Console.WriteLine("")
                            }
                        }
                        else
                        {
                            Console.WriteLine("File does not exists");
                        }
                        break;
                    case4:
                        Console.WriteLine("\n Exiting...");
                        return;
                        default:
                        Console.WriteLine("\n Invalid choice");
                        break;

                 }
            }
        }
    }
}
