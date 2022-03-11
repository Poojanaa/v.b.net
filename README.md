**# List of .Net programs for 1st semester MSc**<br>
**PART-A**<br>
**1.Binary Triangle**<br>
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
using System;<br>
using System.IO;<br>
namespace eXERCISES<br>
{<br>
    class FileRead<br>
    {<br>
        public static void Main()<br>
        {<br>
            string fileName;<br>
            while (true)<br>
            {<br>
                Console.WriteLine("\n_____MENU_____\n");<br>
                Console.WriteLine("\n1.Create a File");<br>
                Console.WriteLine("\n2.Existance of the File");<br>
                Console.WriteLine("\n3.Read the contents of the File");<br>
                Console.WriteLine("\n4.Exit");<br>
                Console.Write("\n Enter your choice:");<br>
                int ch = int.Parse(Console.ReadLine());<br>
                switch (ch)<br>
                {<br>
                    case 1:<br>
                Console.Write("\n Enter the file name to create:");<br>
                fileName = Console.ReadLine();<br>
                Console.WriteLine("\n Write the Contents to the File:\n");<br>
                string r = Console.ReadLine();<br>
                using (StreamWriter fileStr = File.CreateText(fileName))<br>
                {<br>
                    fileStr.WriteLine(r);<br>
                }<br>
                Console.WriteLine("File is Created...");<br>
                break;<br>
                case 2:<br>
                Console.Write("\n Enter the file name:");<br>
                fileName = Console.ReadLine();<br>
                if (File.Exists(fileName))<br>
                {<br>
                    Console.WriteLine("File exists...");<br>
                }<br>
                else<br>
                {<br>
                    Console.WriteLine("File does not exist in the current directory!");<br>
                }<br>
                break;<br>
                case 3:<br>
                Console.Write("Enter the file name to read the contents:\n");<br>
                fileName = Console.ReadLine();<br>
                if (File.Exists(fileName))<br>
                {<br>
                    using (StreamReader sr = File.OpenText(fileName))<br>
                    {<br>
                        string s = "";<br>
                        Console.WriteLine("Here is the content of the file:");<br>
                        while ((s = sr.ReadLine()) != null)<br>
                        {<br>
                            Console.WriteLine(s);<br>
                        }<br>
                        Console.WriteLine("");<br>
                    }<br>
                }<br>
                else<br>
                {<br>
                    Console.WriteLine("File does not exists");<br>
                }<br>
                break;<br>
                case 4:<br>
                Console.WriteLine("\n Exiting...");<br>
                return;<br>
                default :<br>
                      Console.WriteLine("\n Invalid choice");<br>
                break;<br>
                }<br>
            }<br>
        }<br>
    }<br>
}<br>
<br>
<br>
**Output:-**<br>

_____MENU_____<br>


1.Create a File<br>

2.Existance of the File<br>

3.Read the contents of the File<br>

4.Exit<br>

 Enter your choice:2<br>

 Enter the file name:Newfile.txt<br>
File exists...<br>

_____MENU_____<br>


1.Create a File<br>

2.Existance of the File<br>

3.Read the contents of the File<br>

4.Exit<br>

 Enter your choice:3<br>
Enter the file name to read the contents:<br>
Newfile.txt<br>
Here is the content of the file:<br>
Hello...How are you??<br>


_____MENU_____<br>


1.Create a File<br>

2.Existance of the File<br>

3.Read the contents of the File<br>

4.Exit<br>

 Enter your choice:4<br>

 Exiting...<br>
 <br>
 <br>
 **12.Program to perform file comparison**<br>
 using System;<br>
using System.IO;<br>
namespace Exercises<br>
{<br>
    class FileRead<br>
    {<br>
        public static void Main()<br>
        {<br>
            string file1;<br>
            string file2;<br>
            Console.Write("Enter the first file path:");<br>
            file1 = Console.ReadLine();<br>
            Console.Write("Enter the second file path:");<br>
            file2 = Console.ReadLine();<br>
            if(!File.Exists(file1))<br>
            {<br>
                Console.WriteLine("First file does not exists!");<br>
            }<br>
            else if (!File.Exists(file2))<br>
            {<br>
                Console.WriteLine("second file does not exist");<br>
            }<br>
            else if(File.ReadAllText(file1)==File.ReadAllText(file2))<br>
            {<br>
                Console.WriteLine("Both files contain the same content");<br>
            }<br>
            else<br>
            {<br>
                Console.WriteLine("Contents of files are not same");<br>
            }<br>
        }<br>
    }<br>
}<br>
<br>
<br>
**Output:-**<br>
Enter the first file path:C:\Users\ADMIN\Desktop\1st msc\file comparision\F1.txt<br>
Enter the second path:C:\Users\ADMIN\Desktop\1st msc\file comparision\F2.txt<br>
Both files contain the same content<br>
<br>
Enter the first file path:C:\Users\ADMIN\Desktop\1st msc\file comparision\f1.txt<br>
Enter the second path:C:\Users\ADMIN\Desktop\1st msc\file comparision\f3.txt<br>
Contents of the files are not same<br>
<br>
**13.Program to implement Icomparable interface.**<br>
using System;<br>
namespace Exercises<br>
{<br>
    class Fraction : IComparable<br>
    {<br>
        int z, n;<br>
        public Fraction(int z, int n)<br>
        {<br>
            this.z = z;<br>
            this.n = n;<br>
        }<br>
        public static Fraction operator +(Fraction a, Fraction b)<br>
        {<br>
            return new Fraction(a.z * b.n + a.n * b.z, a.n * b.n);<br>
        }<br>
        public static Fraction operator *(Fraction a, Fraction b)<br>
        {<br>
            return new Fraction(a.z * b.z, a.n * b.n);<br>
        }<br>
        public int CompareTo(object obj)<br>
        {<br>
            Fraction f = (Fraction)obj;<br>
            if ((float)z / n < (float)f.z / f.n)<br>
                return -1;<br>
            else if ((float)z / n > (float)f.z / f.n)<br>
                return 1;<br>
            else<br>
                return 0;<br>
        }<br>
        public override string ToString()<br>
        {<br>
            return z + "/" + n;<br>
        }<br>
    }<br>
    class ICompInterface<br>
    {<br>
        public static void Main()<br>
        {<br>
            Fraction[] a =<br>
            {<br>
                new Fraction(5,2),<br>
                new Fraction(29,6),<br>
                new Fraction(4,5),<br>
                new Fraction(10,8),<br>
                new Fraction(34,7)<br>
            };<br>
            Array.Sort(a);<br>
            Console.WriteLine("Implementing the IComparable interface in" + "Displaying Fraction:");<br>
            foreach (Fraction f in a)<br>
            {<br>
                Console.WriteLine(f + " ");<br>

            }<br>
            Console.WriteLine();<br>
            Console.ReadLine();<br>
        }<br>
    }<br>
}<br><br>
<br><br>
**Output:-**<br><br>
Implementing the IComparable interface inDisplaying Fraction:<br>
4/5<br>
10/8<br>
5/2<br>
29/6<br>
34/7<br>
<br>
<br>
**14.Program to create thread pools**<br>
using System;<br>
using System.Threading;<br>
namespace Exercises<br>
{<br>
    class ThreadPoolProg<br>
    {<br>
        public void ThreadFun1(object obj)<br>
        {<br>
            int loop = 0;<br>
            for (loop=0;loop<=4;loop++)<br>
            {<br>
                Console.WriteLine("Thread1 is executing");<br>
            }<br>
        }<br>
        public void ThreadFun2(object obj)<br>
        {<br>
            int loop = 0;<br>
            for(loop=0;loop<=4;loop++)<br>
            {<br>
                Console.WriteLine("Thread2 is executing");<br>
            }<br>
        }<br>
        public static void Main()<br>
        {<br>
            ThreadPoolProg TP = new ThreadPoolProg();<br>
            for(int i=0;i<2;i++)<br>
            {<br>
                ThreadPool.QueueUserWorkItem(new WaitCallback(TP.ThreadFun1));<br>
                ThreadPool.QueueUserWorkItem(new WaitCallback(TP.ThreadFun2));<br>
            }<br>
            Console.ReadKey();<br>
        }<br>
    }<br>
}<br>
<br>
**Output:-**<br>
Thread2 is executing<br>
Thread2 is executing<br>
Thread2 is executing<br>
Thread2 is executing<br>
Thread2 is executing<br>
Thread2 is executing<br>
Thread1 is executing<br>
Thread1 is executing<br>
Thread1 is executing<br>
Thread1 is executing<br>
Thread1 is executing<br>
Thread2 is executing<br>
Thread2 is executing<br>
Thread2 is executing<br>
Thread2 is executing<br>
Thread1 is executing<br>
Thread1 is executing<br>
Thread1 is executing<br>
Thread1 is executing<br>
Thread1 is executing<br>
<br>
<br>
**15.Program to demonstrate error handling usingt try,catch and finally block**<br>
using System;<br>
namespace Exercises<br>
{<br>
    class ExceptionHandling<br>
    {<br>
        static void Main(string[]args)<br>
        {<br>
            Age a = new Age();<br>
            try<br>
            {<br>
                a.displayAge();<br>
            }<br>
            catch(AgeIsNegativeException e)<br>
            {<br>
                Console.WriteLine("AgeIsNegative Exception:{0}", e.Message);<br>
            }<br>
            finally<br>
            {<br>
                Console.WriteLine("Execution of Finally Block is done.");<br>
            }<br>
        }<br>
    }<br>
}<br>
public class AgeIsNegativeException : Exception<br>
{<br>
    public AgeIsNegativeException(string message):base (message)<br>
    {<br>

    }
}<br>
public class Age<br>
{<br>
    int age = -5;<br>
    public void displayAge()<br>
    {<br>
        if (age < 0)<br>
        {<br>
            throw (new AgeIsNegativeException("Age cannot be negative"));<br>
        }<br>
        else<br>
        {<br>
            Console.WriteLine("Age is:{0}", age);<br>
        }<br>
    }<br>
}<br>
<br>
**Output:-**<br>
AgeIsNegative Exception:Age cannot be negative<br>
Execution of Finally Block is done.<br>
<br>
<br>
**16.Write a program to print fibonacci series**<br>
using System;<br>
public class FibonacciExample<br>
{<br>
    public static void Main(string[] args)<br>
    {<br>
        int n1 = 0, n2 = 1, n3, i, number;<br>
        Console.Write("Enter the number of elements:");<br>
        number = int.Parse(Console.ReadLine());<br>
        Console.Write(n1 + "" + n2 + "");<br>
        for(i=2;i<number;++i)<br>
        {<br>
            n3 = n1 + n2;<br>
            Console.Write(n3 + "");<br>
            n1 = n2;<br>
            n2 = n3;<br>
        }<br>
    }<br>
}<br>
<br>
**Output:-**<br>
Enter the number of elements:15<br>
0 1 1 2 3 5 8 13 21 34 55 89 144 233 377<br>
<br>
<br>
**17.Write a program to check prime number**<br>
using System;<br>
public class PrimeNumberExample<br>
{<br>
    public static void Main(string[] args)<br>
    {<br>
        int n, i, m = 0, flag = 0;<br>
        Console.Write("Enter the number to check Prime:");<br>
        n = int.Parse(Console.ReadLine());<br>
        m = n / 2;<br>
        for(i=2;i<=m;i++)<br>
        {<br>
            if(n%i==0)<br>
            {<br>
                Console.Write("Number is not Prime.");<br>
                flag = 1;<br>
                break;<br>
            }<br>
        }<br>
        if (flag == 0)<br>
            Console.Write("Number is Prime.");<br>
    }<br>
}<br>
<br>
**Output:-**<br>
Enter the number to check Prime:17<br>
Number is Prime.<br>
Enter the number to check Prime:57<br>
Number is not Prime.<br>
<br>
<br>
**18.Write a program to check palindrome number**<br>
using System;<br>
public class PalindromeExample<br>
{<br>
    public static void Main(string[] args)<br>
    {<br>
        int n, r, sum = 0, temp;<br>
        Console.Write("Enter the number:");<br>
        n = int.Parse(Console.ReadLine());<br>
        temp = n;<br>
        while(n>0)<br>
        {<br>
            r = n % 10;<br>
            sum = (sum * 10) + r;<br>
            n = n / 10;<br>
        }<br>
        if (temp == sum)<br>
            Console.Write("Number is Palindrome.");<br>
        else<br>
            Console.Write("Number is not Palindrome.");<br>
    }<br>
}<br>
**Output:-**<br>
Enter the number:121<br>
Number is Palindrome.<br>
<br>
Enter the number:123<br>
Number is not Palindrome.<br>
<br>
<br>
**19.Write a program to print factorial of a number**<br>
using System;<br>
public class FactorialExample<br>
{<br>
    public static void Main(string[] args)<br>
    {<br>
        int i, fact = 1, number;<br>
        Console.Write("Enter any Number:");<br>
        number = int.Parse(Console.ReadLine());<br>
        for(i=1;i<=number;i++)<br>
        {<br>
            fact = fact * i;<br>
        }<br>
        Console.Write("Factorial of" + number + "is:" + fact);<br>
    }<br>
}<br>
<br>
**Output:-**<br>
Enter any Number:6<br>
Factorial of6is:720<br>
<br>
<br>
**20.Write a program to check armstrong number**<br>
using System;<br>
public class ArmstrongExample<br>
{<br>
    public static void Main(string[] args)<br>
    {<br>
        int n,r,sum=0,temp;<br>
        Console.Write("Enter the number=");<br>
        n=int.Parse(Console.ReadLine());<br>
        temp=n;<br>
        while(n>0)<br>
        {<br>
            r=n%10;<br>
            sum=sum+(r* r* r);<br>
            n=n/10;<br>
        }<br>
        if (temp == sum)<br>
             Console.Write("Armstrong Number.");<br>
        else<br>
             Console.Write("Not Armstrong Number.");<br>
     }<br>
}<br>
**Output:-**<br>
Enter the number=371<br>
Armstrong Number.<br>
Enter the number=342<br>
Not Armstrong Number.<br>
<br>
<br>
**21.write program to print sum of digits.**<br>
using System;<br>
public class SumExample<br>
{<br>
    public static void Main(string[] args)<br>
    {<br>
        int n, sum = 0, m;<br>
        Console.Write("Enter a number:");<br>
        n = int.Parse(Console.ReadLine());<br>
        while(n>0)<br>
        {<br>
            m = n % 10;<br>
            sum = sum + m;<br>
            n = n / 10;<br>
        }<br>
        Console.Write("Sum is=" + sum);<br>
    }<br>
}<br>
<br>
**Output:-**<br>
Enter a number:23<br>
Sum is=5<br>
<br>
Enter a number:642<br>
Sum is=12<br>
<br>
<br>
**22.Write a program to reverse given number**<br>
using System;<br>
public class ReverseExample<br>
{<br>
    public static void Main(string[] args)<br>
    {<br>
        int n, reverse = 0, rem;<br>
        Console.Write("Enter a number:");<br>
        n = int.Parse(Console.ReadLine());<br>
        while(n!=0)<br>
        {<br>
            rem = n % 10;<br>
            reverse = reverse * 10 + rem;<br>
            n/=10;<br>
        }<br>
        Console.Write("Reversed Number:" + reverse);<br>
    }<br>
}<br>
<br>
**Output:-**<br>
Enter a number:234<br>
Reversed Number:432<br>
<br>
<br>
**PART-B**<br>
**23.Write a program to convert Digits to Words.**<br>
![image](https://user-images.githubusercontent.com/98141711/157806529-5fea4d89-1535-4e4b-b903-472b5c793ed9.png)<br>
using System;<br>
using System.Collections.Generic;<br>
using System.ComponentModel;<br>
using System.Data;<br>
using System.Drawing;<br>
using System.Linq;<br>
using System.Text;<br>
using System.Threading.Tasks;<br>
using System.Windows.Forms;<br>

namespace digittoword<br>
{<br>
    public partial class Form1 : Form<br>
    {<br>
        public Form1()<br>
        {<br>
            InitializeComponent();<br>
        }<br>

        private void button1_Click(object sender, EventArgs e)<br>
        {<br>
            label1.Text = NumtoWord(long.Parse(txt_num.Text));<br>
            label1.Visible = true;<br>
        }<br>
        public string NumtoWord(long number)<br>
        {<br>
            string word = "";
            if(number==0)<br>
            {<br>
                return "{Zero";<br>
            }<br>
            if(number<0)<br>
            {<br>
                return "Minus" + Math.Abs(number);<br>
            }<br>
            if(number/1000000>0)<br>
            {<br>
                word += NumtoWord(number / 10000000) + "Corer";<br>
                number %= 10000000;<br>
            }<br>
            if(number/100000>0)<br>
            {<br>
                word += NumtoWord(number / 100000) + "Lacs";<br>
                number %= 100000;<br>
            }<br>
            if(number/100>0)<br>
            {<br>
                word += NumtoWord(number / 100) + "Hundred";<br>
                number %= 100;<br>
            }<br>
            if(number>0)<br>
            {<br>
                string[] units = new string[] { "Zero", "One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine","Ten","Eleven", "Twelve", "Thirteen", "Fourteen", "Fifteen", "Sixteen", "Seventeen", "Eighteen", "Nineteen" };<br>
                string[] Tens = new string[] { "Zero", "Ten", "Twenty", "Thirty", "Fourty", "Fifty", "Sixty", "Seventy", "Eighty", "Ninety" };<br>
                if(number<20)<br>
                {<br>
                    word += units[number];<br>
                }<br>
                else<br>
                {<br>
                    word += Tens[number / 10];<br>
                    if(number%10>0)<br>
                    {<br>
                        word += units[number % 10];<br>
                    }<br>
                }<br>
            }<br>
            return word;<br>
        }<br>
    }<br>
}<br>
<br>
**output:-**<br>
![image](https://user-images.githubusercontent.com/98141711/157806406-4ae04125-0af1-4742-a06e-f0355418dbec.png)<br>
<br>
<br>








    

 
