### Delegate
- 메서드를 참조하는 객체로 메서드의 시그니처(입력 변수와 반환 타입)에 대한 정보를 포함한다. 이를 통해 런타임에 해당 시그니처를 갖는 메서드를 호출할 수 있다.
```csharp
public delegate float CustomDelegate(int a, int b);

public class MyClass
{
    public static float Divide(int a, int b)
    {
        return (float)a / b;
    }
}

public class MainClass
{
    public static void Main()
    {
        CustomDelegate del = MyClass.Divide;
        float result = del(10, 5);
        Console.WriteLine("Result: " + result);
    }
}
```
### Func
- Func는 반환 타입이 void가 아닌 0 ~ n개의 매개변수를 가진 함수를 나타내는 제네릭 델리게이트이다.
```csharp
public class MyClass
{
    public static int GetNumber()
    {
        return 42;
    }

    public static string ToString(int number)
    {
        return "Number: " + number;
    }
}

public class MainClass
{
    public static void Main()
    {
        Func<int> numberFunc = MyClass.GetNumber;
        int number = numberFunc();
        Console.WriteLine("Number: " + number);

        Func<int, string> toStringFunc = MyClass.ToString;
        string result = toStringFunc(42);
        Console.WriteLine(result);
    }
}
```
### Action
- Action은 반환 타입이 void인 메소드를 위해 설계된 제네릭 델리게이트이다. 
```csharp
public class MyClass
{
    public static void PrintHello()
    {
        Console.WriteLine("Hello!");
    }

    public static void PrintSum(float a, float b)
    {
        Console.WriteLine("Sum: " + (a + b));
    }
}

public class MainClass
{
    public static void Main()
    {
        Action helloAction = MyClass.PrintHello;
        helloAction();

        Action<float, float> sumAction = MyClass.PrintSum;
        sumAction(3.5f, 5.5f);
    }
}
```