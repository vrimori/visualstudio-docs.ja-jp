---
title: "クイック アクション | Microsoft Docs"
ms.custom: 
ms.date: 05/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 22a6c84608f8955e3a751af4ee2b9fb113645590
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="quick-actions"></a>クイック アクション

[クイック アクション](refactoring-code-generation-quick-actions.md#quick-actions)を使うと、コードのリファクタリング、生成、その他の変更を、1 つの操作で簡単に行うことができます。 クイック アクションは、C#、[C++](/cpp/ide/writing-and-refactoring-code-cpp)および Visual Basic のコード ファイルで使用できます。 クイック アクションには、言語に固有のものと、すべての言語が対象になるものがあります。 クイック アクションは、電球アイコン ![小さい電球アイコン](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") を使うか、または適切なコード行にカーソルを置いて **Ctrl** + **.** キーを押すと 適用できます。

赤い波線が表示され、Visual Studio が問題の修正候補を提供できる場合に、電球アイコンが表示されます。 たとえば、赤い波線で示されるエラーがある場合、そのエラーの修正が可能な場合に電球マークが表示されます。 いずれの言語でも、サードパーティは、たとえば SDK の一部として、カスタマイズした診断や提案を表示できます。Visual Studio はそれらの規則に基づいて電球マークを表示します。

## <a name="to-see-a-light-bulb"></a>電球マークを表示するには

1. 多くの場合、電球マークはマウスをエラーの地点に移動すると自動的に表示されます。あるいは、カレットをエラーのある行に移動すると、エディターの左端に表示されます。 赤い波線が表示されている場合にマウス ポインターを重ねると電球マークを表示させることができます。 問題が発生した行のどこかに、マウスやキーボードを使用して移動することで電球マークを表示させることもできます。

1. 行の任意の場所で **Ctrl** + **.** キーを押すと、 電球マークの表示を呼び出して修正候補のリストを直接表示できます。

   ![電球でのマウス ホバー](../ide/media/vs2015_lightbulb_hover.png "VS2017_LightBulb_Hover")

## <a name="to-see-potential-fixes"></a>修正候補を表示するには

下矢印をクリックするか、修正候補を表示するリンクをクリックすると、電球マークで実行可能なクイック操作のリストが表示されます。

![拡大電球](../ide/media/vs2015_lightbulb_hover_expanded.png "VS2017_LightBulb_hover_expanded")

## <a name="common-quick-actions"></a>共通のクイック アクション

ここでは、C# と Visual Basic 両方のコードに共通に適用されるクイック アクションを示します。
- [エラーを修正するアクション](#fix)
- [不要なコードを削除するアクション](#remove)
- [不足しているコードを追加するアクション](#add)
- [コード変換](#transform)

### <a id="fix"></a> エラーを修正するアクション

#### <a name="correct-misspelled-type"></a>スペルが正しくない型を修正する
|  エラー ID | 該当言語 |  サポートされているバージョン |
| ------- | -------------------- | ----------------  |
| CS0103、BC30002 | C# および Visual Basic | Visual Studio 2015 更新プログラム 2 |

Visual Studio で型のスペルを誤って入力した場合、このクイック アクションは自動的にそれを修正します。  電球メニューでは **['*スペルが正しくない型*' を '*スペルが正しい型*' に変更]** と表示されます。  例:

```csharp
// Before
private viod MyMethod()
{
}

// Change 'viod' to 'void'

// After
private void MyMethod()
{
}
```

```vb
' Before
Function MyFunction as Intger
End Function

' Change 'Intger' to 'Integer'

' After
Function MyFunction as Integer
End Function
```

#### <a name="resolve-git-merge-conflict"></a>git のマージ競合を解決する
|  エラー ID | 該当言語 |  サポートされているバージョン |
| ------- | -------------------- | ----------------  |
| CS8300、BC37284  | C# および Visual Basic | Visual Studio 2017 バージョン 15.3 |

このクイック アクションを使用すると、"変更を取り入れる" ことで競合するコードおよびマーカーが削除され、git マージ競合を解決することができます。  

```csharp
// Before     
private void MyMethod()
{
<<<<<<< HEAD
    if (true)
    {

    }
=======
    if (false)
    {

    }
>>>>>>> upstream
}

// Take changes from 'HEAD'

// After 
private void MyMethod()
{
    if (true)
    {

    }
}
```

#### <a name="make-method-synchronous"></a>メソッドを同期させる
|  エラー ID | 該当言語 |  サポートされているバージョン |
| ------- | -------------------- | ----------------  |
| CS1998、BC42356 | C# および Visual Basic | Visual Studio 2015 更新プログラム 2 |

`async`/`Async` キーワードをメソッドで使う場合は、そのメソッド内のどこかで `await`/`Await` キーワードも使われることが予想されます。  ただし、そうではない場合は、クイック アクションが表示され、`async`/`Async` キーワードを削除して戻り値の型を変更することにより、同期メソッドにすることができます。  [クイック アクション] メニューの **[メソッドを同期させます]** オプションを選びます。

```csharp
// Before
async Task<int> MyAsyncMethod()
{
    return 3;
}

// Make method synchronous

// After
int MyAsyncMethod()
{
    return 3;
}
```

```vb
' Before
Async Function MyAsyncMethod() As Task(Of Integer)
    Return 3
End Function

' Make method synchronous

' After
Function MyAsyncMethod() As Integer
    Return 3
End Function
```

#### <a name="make-method-asynchronous"></a>メソッドを非同期にする
|  エラー ID | 該当言語 |  サポートされているバージョン |
| ------- | -------------------- | ----------------  |
| CS4032、BC37057 | C# および Visual Basic | Visual Studio 2017 |

メソッド内で `await`/`Await` キーワードを使うときは、メソッド自体に `async`/`Async` キーワードが指定されていることが想定されます。  ただし、そうではない場合は、クイック アクションが表示され、非同期メソッドにすることができます。  [クイック アクション] メニューの **[Make method/Function asynchronous (メソッド/関数を非同期にします)]** オプションを使います。

```csharp
// Before
int MyAsyncMethod()
{
    return await Task.Run(...);
}

// Make method asynchronous

// After
async Task<int> MyAsyncMethod()
{
    return await Task.Run(...);
}
```

```vb
' Before
Function MyAsyncMethod() as Integer
    Return  Await Task.Run(...)
End Function

' Make method asynchronous

' After
Async Function MyAsyncMethod() As Task(Of Integer)
    Return Await Task.Run(...)
End Function
```

### <a id="remove"></a> 不要なコードを削除するアクション

#### <a name="remove-unnecesary-usingsimports"></a>不必要な using/Import を削除する

|  該当言語 |  サポートされているバージョン |
|  -------------------- | ----------------  |
|  C# および Visual Basic | Visual Studio 2015 RTW |

**[不要な using の削除] / [不要なインポートの削除]** クイック アクションは、現在のファイルで使われていない `using` および `Import` ステートメントを削除します。  この項目を選ぶと、使われていない名前空間のインポートがすぐに削除されます。

#### <a name="remove-unnecessary-cast"></a>不要なキャストを削除する
|  診断 ID | 該当言語 |  サポートされているバージョン |
| ------- | -------------------- | ----------------  |
| IDE0004 | C# および Visual Basic | Visual Studio 2015 RTW |

ある型をキャストが不要な別の型にキャストしている場合、**[不要なキャストの削除]** クイック アクション項目はキャストをコードから削除します。

```csharp
// before
int number = (int)3;

// Remove Unnecessary Cast

// after
int number = 3;
```
```vb
' Before
Dim number as Integer = CType(3, Integer)

' Remove Unnecessary Cast

' After
Dim number as Integer = 3
```

#### <a name="remove-unused-variables"></a>未使用の変数を削除する
|  診断 ID | 該当言語 |  サポートされているバージョン |
| ------- | -------------------- | ----------------  |
| CS0219、BC42024 | C# および Visual Basic | Visual Studio 2017 バージョン 15.3 |

このクイック アクションでは、宣言されているがコードで一度も使用されていない変数を削除することができます。

```csharp
// Before
public MyMethod()
{
    var unused = 8;
    var used = 1;
    return DoStuff(used);
}

// Remove unused variables

// After
public MyMethod()
{
    var used = 1;
    return DoStuff(used);
}
```

#### <a name="remove-type-from-default-value-expression"></a>**既定**の値式から型を削除する
|  診断 ID | 該当言語 |  サポートされているバージョン |
| ------- | -------------------- | ----------------  |
| IDE0034 | C# 7.1+ | Visual Studio 2017 バージョン 15.3 |

このクイック アクションは、コンパイラが式の型を推論できる場合に、既定の値式から値の型を削除し、[`default`リテラル](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference)を使用します。

```csharp 
// Before
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }

// Simplify default expression

// After
void DoWork(CancellationToken cancellationToken = default) { ... }

```

### <a id="add"></a> 不足しているコードを追加するアクション

#### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>参照アセンブリの型、NuGet パッケージの型、またはソリューション内の他の型に using/Import を追加する
|  診断 ID | 該当言語 |  サポートされているバージョン |
| ------- | -------------------- | ----------------  |
| CS0103、BC30451 | C# および Visual Basic| Visual Studio 2015 更新プログラム 2 |

ソリューション内の他のプロジェクトにある型を使うとクイック アクションが自動的に表示されますが、それ以外の場合は **[ツール] > [オプション] > [C#]** または **[Basic] > [詳細設定]** タブで有効にする必要があります。  

* 参照アセンブリの型に using/import を提案する
* NuGet パッケージの型に using/import を提案する

有効にした場合、現在はインポートされていなくても参照アセンブリまたは NuGet パッケージには存在する名前空間の型を使うと、using/import ステートメントが作成されます。

```csharp
// Before
Debug.WriteLine("Hello");

// using System.Diagnostics;

// After
using System.Diagnostics;

Debug.WriteLine("Hello");
```

```vb
' Before
Debug.WriteLine("Hello")

' Imports System.Diagnostics

// After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

#### <a name="add-missing-casesdefault-caseboth"></a>足りないケース、既定のケース、または両方を追加する
|  診断 ID | 該当言語 |  サポートされているバージョン |
| ------- | -------------------- | ----------------  |
| IDE0010 | C# および Visual Basic| Visual Studio 2017 バージョン 15.3 |

`switch` ステートメント (C#) または `Select Case` ステートメント (Visual Basic) を作成するときは、コード アクションを使って、足りないケース項目、既定のケースのステートメント、または両方を自動的に追加できます。  空のステートメントは次のようになります。

```csharp
enum MyEnum
{
    Item1,
    Item2,
    Item3
}

...

MyEnum myEnum = MyEnum.Item1;

switch(myEnum)
{
}
```

```vb
Enum MyEnum
    Item1
    Item2
    Item3
End Enum

...

Dim myEnum as MyEnum = MyEnum.Item1

Select Case myEnum
End Select
```

**[両方を追加する]** クイック アクションを使って足りないケースと既定のケースの両方を追加すると、次のようなコードが作成されます。

```csharp
switch(myEnum)
{
    case MyEnum.Item1:
        break;
    case MyEnum.Item2:
        break;
    case MyEnum.Item3:
        break;
    default:
        break;
}
```
```vb
Select Case myEnum
    Case MyEnum.Item1
        Exit Select
    Case MyEnum.Item2
        Exit Select
    Case Else
        Exit Select
End Select
```

#### <a name="add-null-checks-for-parameters"></a>パラメーターの null チェックを追加する
| 該当言語 |  サポートされているバージョン |
| -------------------- | ----------------  |
| C# および Visual Basic| Visual Studio 2017 バージョン 15.3 |

このクイック アクションでは、パラメーターが null であるかどうかを示すチェックをコードに追加できます。

```csharp
// Before
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty) // cursor inside myProperty
    {
        MyProperty = myProperty;
    }
}

// Add null check

// After
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty)
    {
        MyProperty = myProperty ?? throw new ArgumentNullException(nameof(myProperty));
    }
}
```

#### <a name="add-argument-name"></a>引数の名前を追加する
| 該当言語 |  サポートされているバージョン |
| -------------------- | ----------------  |
| C# および Visual Basic| Visual Studio 2017 バージョン 15.3 |

```csharp
// Before
var date = new DateTime(1997, 7, 8);

// Include argument name 'year' (include trailing arguments)

// After
var date = new DateTime(year: 1997, month: 7, day: 8);
```

#### <a name="add-braces"></a>中かっこを追加する
|  診断 ID | 該当言語 |  サポートされているバージョン |
| ------- | -------------------- | ----------------  |
| IDE0011 | C# | Visual Studio 2017 RTW |

"中かっこを追加する" クイック アクションは、単一行の `if` ステートメントを中かっこで囲みます。

```csharp
// Before
if (true)
    return "hello,world";

// Add braces

// After
if (true) 
{
    return "hello,world";
}
```

#### <a name="add-and-order-modifiers"></a>修飾子を追加および順序付けする
|  診断 ID | 該当言語 |  サポートされているバージョン |
| ------- | -------------------- | ----------------  |
| IDE0036 | C# および Visual Basic| Visual Studio 2017 バージョン 15.5 |
| IDE0040 | C# および Visual Basic| Visual Studio 2017 バージョン 15.5 |

これらのクイック アクションを使用すると、既存のアクセシビリティ修飾子の並べ替えや、不足しているアクセシビリティ修飾子の追加が行えるようになり、修飾子を整理するのに便利です。

```csharp
// Before
enum Color
{
    Red, White, Blue
}

// Add accessibility modifiers

// After
internal enum Color
{
    Red, White, Blue
}
```
```csharp
// Before
static private int thisFieldIsPublic;

// Order modifiers

// After
private static int thisFieldIsPublic;

```

### <a id="transform"></a> コード変換

#### <a name="convert-if-construct-to-switch"></a>**if** コンストラクトを **switch** に変換する
| 該当言語 |  サポートされているバージョン |
| -------------------- | ----------------  |
| C# および Visual Basic| Visual Studio 2017 バージョン 15.3 |

このクイック アクションでは、**if-then-else** コンストラクトを **switch** コンストラクトに変換することができます。

```csharp
// Before
if (obj is string s)
{
  Console.WriteLine("obj is a string: " + s);
}

else if (obj is int i && i > 10)
{
  Console.WriteLine("obj is an int greater than 10");
}

// Convert to switch

// After
switch (obj)
{
  case string s:
    Console.WriteLine("Obj is a string: " + s);
    break;
  case int i when i > 10:
    Console.WriteLine("obj is an int greater than 10");
    break;
}
```

```vb
' Before
If TypeOf obj Is String s Then
    Console.WriteLine("obj is a string: " + s)
Else If TypeOf obj Is Integer i And i > 10 Then
    Console.WriteLine("obj is an int greater than 10")
End If

' Convert to switch

' After
Select Case obj
  Case String s
    Console.WriteLine("Obj is a string: " + s)
    Exit Sub
  Case Integer i when i > 10
    Console.WriteLine("obj is an int greater than 10")
    Exit Sub
End Select
```

#### <a name="convert-to-interpolated-string"></a>挿入文字列に変換する
| 該当言語 |  サポートされているバージョン |
| -------------------- | ----------------  |
| C# 6.0+ および Visual Basic 14+ | Visual Studio 2017 RTW |

[挿入文字列](/dotnet/csharp/language-reference/keywords/interpolated-strings)は、埋め込み変数を含む文字列を表現する簡単な方法であり、**[String.Format](https://msdn.microsoft.com/library/system.string.format.aspx)** メソッドに似ています。  このクイック アクションは、文字列が連結されている場合、または **String.Format** が使われている場合を認識し、それを挿入文字列に変更します。

```csharp
// Before
int num = 3;
string s = string.Format("My string with {0} in the middle", num);

// Convert to interpolated string

// After
int num = 3;
string s = $"My string with {num} in the middle";
```
```vb
' Before
Dim num as Integer = 3
Dim s as String = String.Format("My string with {0} in the middle", num)

' Convert to interpolated string

' After
Dim num as Integer = 3
Dim s As String = $"My string with {num} in the middle"
```

#### <a name="use-object-initializers"></a>オブジェクト初期化子を使用する
| 診断 ID | 該当言語 | サポートされているバージョン |
| ------- | -------------------- | ----------------  |
| IDE0017 | C# および Visual Basic | Visual Studio 2017 RTW |

このクイック アクションでは、コンストラクターを呼び出して代入ステートメントの行を追加するのでなく、[オブジェクト初期化子](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)を使用することができます。

```csharp
// Before
var c = new Customer();
c.Age = 21;

// Object initialization can be simplified

// After
var c = new Customer() { Age = 21 };
```
```vb
' Before
Dim c = New Customer()
c.Age = 21

' Object initialization can be simplified

' After
Dim c = New Customer() With {.Age = 21}
```

#### <a name="use-collection-initializers"></a>コレクション初期化子を使用する
| 診断 ID | 該当言語 | サポートされているバージョン |
| ------- | -------------------- | ----------------  |
| IDE0028 | C# および Visual Basic | Visual Studio 2017 RTW |

このクイック アクションでは、クラスの `Add` メソッドを複数回呼び出すのではなく、[コレクション初期化子](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)を使用することができます。

```csharp
// Before
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);

// Collection initialization can be simplified

// After
var list = new List<int> { 1, 2, 3 };
```
```vb
' Before
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)

' Collection initialization can be simplified

' After
Dim list = New List(Of Integer) From {1, 2, 3}

```  

#### <a name="convert-auto-property-to-full-property"></a>自動プロパティを完全なプロパティに変換する
|  該当言語 |  サポートされているバージョン |
|  -------------------- | ----------------  |
| C# および Visual Basic | Visual Studio 2017 バージョン 15.5 |

このクイック アクションでは、自動プロパティから完全なプロパティへの変換、またはその逆の変換を行うことができます。

```csharp
// Before
private int MyProperty { get; set; }

// Convert to full property

// After
private int MyProperty
{
    get { return _myProperty; }
    set { _myProperty = value; } 
}
```
```vb
' Before
Public Property Name As String

' Convert to full property

' After
Private _Name As String

Public Property Name As String
    Get
        Return _Name
    End Get
    Set
        _Name = Value
    End Set
End Property

```

#### <a name="convert-block-body-to-expression-bodied-member"></a>ブロック本体を式のようなメンバーに変換する
|  診断 ID | 該当言語 |  サポートされているバージョン |
| ------- | -------------------- | ----------------  |
| IDE0021-27 | C# 6.0+ | Visual Studio 2017 RTW |

このクイック アクションではブロック本体を、メソッド、コンストラクター、演算子、プロパティ、インデクサー、およびアクセサー用の式のようなメンバーに変換します。

```csharp
//Before
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get { return _myProperty; }
        set
        {
            _myProperty = value;
        }
    }

    public MyClass4(int myProperty)
    {
        MyProperty = myProperty;
    }

    public void PrintProperty()
    {
        Console.WriteLine(MyProperty);
    }
}

// Use expression body for accessors/constructors/methods

// After
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get => _myProperty;
        set => _myProperty = value;
    }

    public MyClass4(int myProperty) => MyProperty = myProperty;

    public void PrintProperty() => Console.WriteLine(MyProperty);
}
```

#### <a name="convert-anonymous-function-to-local-function"></a>匿名関数をローカル関数に変換する
|  診断 ID | 該当言語 |  サポートされているバージョン |
| ------- | -------------------- | ----------------  |
| IDE0039 | C# 7.0+ | Visual Studio 2017 バージョン 15.5 |

このクイック アクションは、匿名関数をローカル関数に変換します。

```csharp 
// Before
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};

// Use local function

// After
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}

```

#### <a name="convert-referenceequals-to-is-null"></a>`ReferenceEquals` を `is null` に変換する
|  診断 ID | 該当言語 |  サポートされているバージョン |
| ------- | -------------------- | ----------------  |
| IDE0041 | C# 7.0+ | Visual Studio 2017 バージョン 15.5 |

このクイック アクションでは、可能な限り、```ReferenceEquals``` コーディング パターンではなく、[パターン マッチング](/dotnet/csharp/pattern-matching)の使用を提案します。

```csharp
// Before
var value = "someString";
if (object.ReferenceEquals(value, null))
{
    return;
}

// Use 'is null' check

// After
var value = "someString";
if (value is null)
{
    return;
}
```

#### <a name="introduce-pattern-matching"></a>パターン マッチングを導入する
| 診断 ID | 該当言語 | サポートされているバージョン |
| ------- | -------------------- | ----------------  |
| IDE0020 | C# 7.0+ | Visual Studio 2017 RTW |
| IDE0019 | C# 7.0+ | Visual Studio 2017 RTW |

このクイック アクションでは、C# におけるキャストおよび null チェックで、[パターン マッチング](/dotnet/csharp/pattern-matching)の使用を提案します。   

```csharp
// Before
if (o is int) 
{
    var i = (int)o; 
    ... 
}

// Use pattern matching

// After
if (o is int i) 
{
    ...
}

```
```csharp
// Before
var s = o as string;
if (s != null) 
{
    ...
}

// Use pattern matching

// After
if (o is string s) 
{
    ...
}
```

#### <a name="change-base-for-numeric-literals"></a>数値リテラルの基本を変更する
| 該当言語 | サポートされているバージョン |
| ------- | -------------------- | ----------------  |
| C# 7.0+ および Visual Basic 14+ | Visual Studio 2017 バージョン 15.3 |

このクイック アクションでは、数値リテラルの基本数値システムを別のものに変換できます。 たとえば、数値を 16 進数からバイナリ形式に変更できます。 

```csharp
// Before
int countdown = 2097152;

// Convert to hex

// After
int countdown = 0x200000;
```
```vb
' Before
Dim countdown As Integer = 2097152

' Convert to hex

' After
Dim countdown As Integer = &H200000
```

#### <a name="insert-digit-separators-into-literals"></a>リテラルに桁区切り記号を挿入する
| 該当言語 | サポートされているバージョン |
| ------- | -------------------- | ----------------  |
| C# 7.0+ および Visual Basic 14+ | Visual Studio 2017 バージョン 15.3 |

このクイック アクションでは、区切り文字をリテラル値に追加することができます。  

```csharp
// Before
int countdown = 1000000;

// Separate thousands

// After
int countdown = 1_000_000;
```
```vb
' Before
Dim countdown As Integer = 1000000

' Separate thousands

' After
Dim countdown As Integer = 1_000_000
```

#### <a name="use-explicit-tuple-names"></a>明示的なタプル名を使用する
| 診断 ID | 該当言語 | サポートされているバージョン |
| ------- | -------------------- | ----------------  |
| IDE0033 | C# 7.0+ および Visual Basic 15+ | Visual Studio 2017 RTW |

このクイック アクションでは、Item1、Item2 などのタプル名ではなく、明示的なタプル名を使用できる領域を識別します。

```csharp
// Before
(string name, int age) customer = GetCustomer();
var name = customer.Item1;

// Use explicit tuple name

// After
(string name, int age) customer = GetCustomer();
var name = customer.name;
```
```vb
' Before
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1

' Use explicit tuple name

' After
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name
```

#### <a name="use-inferred-names"></a>推論による名前を使用する
| 診断 ID | 該当言語 | サポートされているバージョン |
| ------- | -------------------- | ----------------  |
| IDE0037 | C# | Visual Studio 2017 v. 15.5 |
| IDE0037 | C# 7.1+ | Visual Studio 2017 v. 15.5 |

これらクイック アクションでは、匿名型の推論によるメンバー名を使用、または C# 7.1 の推論によるタプル要素名を使用できるタイミングを指摘します。

```csharp 
// Before
var anon = new { age = age, name = name };

// Use inferred member name

// After
var anon = new { age, name };
```
```csharp
// Before
var tuple = (age: age, name: name);

// Use inferred tuple element name

// After
var tuple = (age, name);

```

#### <a name="deconstruct-tuple-declaration"></a>タプル宣言を分解する
| 診断 ID | 該当言語 | サポートされているバージョン |
| ------- | -------------------- | ----------------  |
| IDE0042 | C# 7.0+ | Visual Studio 2017 v. 15.5 |

このクイック アクションでは、タプル変数宣言を分解することができます。 

```csharp 
// Before
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");

//Deconstruct variable declaration

// After
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");
```

## <a name="see-also"></a>関連項目
* [コード スタイルとクイック アクション](code-styles-and-quick-actions.md)  
* [コードの作成とリファクタリング (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
