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
Student  55 :20210055<br>
Student  56 : 20210056
Student  57 : 20210057
Student  58 : 20210058
Student  59 : 20210059
Student  60 : 20210060
Student  61 : 20210061
Student  62 : 20210062
Student  63 : 20210063
Student  64 : 20210064
Student  65 : 20210065
Student  66 : 20210066
Student  67 : 20210067
Student  68 : 20210068
Student  69 : 20210069
Student  70 : 20210070
Student  71 : 20210071
Student  72 : 20210072
Student  73 : 20210073
Student  74 : 20210074
Student  75 : 20210075
Student  76 : 20210076
Student  77 : 20210077
Student  78 : 20210078
Student  79 : 20210079
Student  80 : 20210080
Student  81 : 20210081
Student  82 : 20210082
Student  83 : 20210083
Student  84 : 20210084
Student  85 : 20210085
Student  86 : 20210086
Student  87 : 20210087
Student  88 : 20210088
Student  89 : 20210089
Student  90 : 20210090
Student  91 : 20210091
Student  92 : 20210092
Student  93 : 20210093
Student  94 : 20210094
Student  95 : 20210095
Student  96 : 20210096
Student  97 : 20210097
Student  98 : 20210098
Student  99 : 20210099
Student  100 : 20210100



