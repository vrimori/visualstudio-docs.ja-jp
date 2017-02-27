---
title: "How to: Split a Class into Partial Classes (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Class Designer, partial classes"
  - "partial classes, Class Designer"
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# How to: Split a Class into Partial Classes (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Basic の `Partial` キーワードまたは Visual C\# の `partial` キーワードを使用すると、1 つのクラスまたは構造体の宣言を複数の宣言に分割できます。  部分宣言は必要に応じていくつでも使用でき、複数のソース ファイルとして作成することも、1 つのソース ファイルに含めることもできます。  しかし、すべての宣言は同じアセンブリと同じ名前空間内にある必要があります。  
  
 部分クラスは、いくつかの状況で役に立ちます。  たとえば、大規模なプロジェクトを開発している場合、1 つのクラスを複数のファイルに分割することで、複数のプログラマが同時にそのクラスの作業を実行できるようになります。  また、Visual Studio が生成したコードを使用している場合に、ソース ファイルを再作成せずにクラスを変更できます   \(Visual Studio が生成するコードの例としては、Windows フォームや Web サービスのラッパー コードなどがあります\)。したがって、Visual Studio が作成したファイルを変更せずに、自動生成されるクラスを使用するコードを作成できます。  
  
 部分メソッドには 2 つの種類があります。  Visual C\# でも Visual Basic でも、これらは宣言および実装と呼ばれます。  
  
 クラス デザイナーでは、部分クラスと部分メソッドがサポートされています。  クラス ダイアグラムでの型シェイプは、部分クラスの 1 つの宣言の場所を参照します。  部分クラスが複数のファイルで定義されている場合、**\[プロパティ\]** ウィンドウで **\[新しいメンバーの場所\]** プロパティを設定することにより、クラス デザイナーが使用する宣言の場所を指定することができます。  つまり、クラスの図形をダブルクリックすると、クラス デザイナーは、**\[新しいメンバーの場所\]** プロパティで識別されるクラス宣言が含まれるソース ファイルに移動します。  また、クラスの図形に含まれている部分メソッドをダブルクリックすると、クラス デザイナーは、部分メソッドの宣言に移動します。  また、**\[プロパティ\]** ウィンドウでは、**\[ファイル名\]** プロパティが宣言の場所を示します。  部分クラスの場合、**\[ファイル名\]** には、宣言を含むファイルと、そのクラスの実装コードのすべてが示されます。  一方、部分メソッドの **\[ファイル名\]** には、部分メソッドの宣言を含むファイルのみが示されます。  
  
 次の例では、クラス `Employee` の定義を 2 つの宣言に分割し、それぞれで別のプロシージャを定義しています。  この例の 2 つの部分定義は、1 つのソース ファイル内にあっても、異なるソース ファイル内にあってもかまいません。  
  
> [!NOTE]
>  Visual Basic は、部分クラスの定義を使用して、Visual Studio が生成するコードとユーザーが作成するコードを分離します。  コードは、別々のソース ファイルに分離されます。  たとえば、**Windows フォーム デザイナー**は、`Form` などのコントロールに部分クラスを定義します。  これらのコントロールでは、生成されたコードを変更しないでください。  
  
 Visual Basic での部分型の詳細については、「[Partial](/dotnet/visual-basic/language-reference/modifiers/partial)」を参照してください。  
  
## 使用例  
 Visual Basic でクラス定義を分割するには、次の例に示すように、`Partial` キーワードを使用します。  
  
```vb#  
' First part of class definition.  
Partial Public Class Employee  
    Public Sub CalculateWorkHours()  
    End Sub  
End Class  
  
' Second part of class definition.  
Partial Public Class Employee  
    Public Sub CalculateTaxes()  
    End Sub  
End Class  
```  
  
## 使用例  
 C\# でクラス定義を分割するには、次の例に示すように、`partial` キーワードを使用します。  
  
```c#  
// First part of class definition.  
public partial class Employee  
{  
    public void CalculateWorkHours()  
    {  
    }  
}  
  
// Second part of class definition.  
public partial class Employee  
{  
    public void CalculateTaxes()  
    {  
    }  
}  
```  
  
## 参照  
 [部分クラスと部分メソッド](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [partial \(型\)](/dotnet/csharp/language-reference/keywords/partial-type)   
 [partial \(メソッド\) \(C\# リファレンス\)](/dotnet/csharp/language-reference/keywords/partial-method)   
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)