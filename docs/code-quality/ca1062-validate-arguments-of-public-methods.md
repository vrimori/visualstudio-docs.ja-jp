---
title: "CA1062: パブリック メソッドの引数の検証 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1062"
  - "ValidateArgumentsOfPublicMethods"
  - "Validate arguments of public methods"
helpviewer_keywords: 
  - "CA1062"
  - "ValidateArgumentsOfPublicMethods"
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1062: パブリック メソッドの引数の検証
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ValidateArgumentsOfPublicMethods|  
|CheckId|CA1062|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## 原因  
 引数が `null` \(Visual Basic では `Nothing`\) であるかどうかを確認せずに、外部から参照可能なメソッドが参照引数の 1 つを逆参照しています。  
  
## 規則の説明  
 外部から参照可能なメソッドに渡されるすべての参照引数について、`null` かどうかをチェックする必要があります。  引数が `null` の場合、<xref:System.ArgumentNullException> をスローします。  
  
 メソッドがパブリックまたはプロテクトとして宣言されているために、未知のアセンブリから呼び出すことができる場合は、そのメソッドのすべてのパラメーターを検証する必要があります。  メソッドが既知のアセンブリからのみ呼び出すことができるよう設計されている場合は、そのメソッドを内部メソッドとして設定し、そのメソッドを含むアセンブリに <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性を適用する必要があります。  
  
## 違反の修正方法  
 この規則違反を修正するには、各参照引数が `null` かどうかを検証します。  
  
## 警告を抑制する状況  
 逆参照されるパラメーターが、関数の別のメソッド呼び出しによって検証されていることが確実な場合は、この規則からの警告を表示しないようにすることができます。  
  
## 使用例  
 この規則に違反しているメソッドと、規則に適合するメソッドを次の例に示します。  
  
 [!code-cs[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_1.cs)]
 [!code-cs[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_1.cs)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/VisualBasic/ca1062-validate-arguments-of-public-methods_1.vb)]  
  
## 使用例  
 [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] では、検証を行う別のメソッドにパラメーターが渡されるかどうかを、この規則で検出できませんでした。  
  
 [!code-cs[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_2.cs)]
 [!code-cs[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_2.cs)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/VisualBasic/ca1062-validate-arguments-of-public-methods_2.vb)]  
  
## 使用例  
 参照オブジェクトであるフィールドまたはプロパティを設定するコピー コンストラクターを実行すると、CA1064 規則に違反する可能性があります。  この違反が発生するのは、コピー コンストラクターに渡されるコピーされたオブジェクトが `null` \(Visual Basic では `Nothing`\) である可能性があるためです。  この違反を解決するには、静的 \(Visual Basic では共有\) メソッドを使用して、コピーされたオブジェクトが null でないことを確認します。  
  
 次の `Person` クラスの例では、`Person` コピー コンストラクターに渡される `other` オブジェクトが `null` である可能性があります。  
  
```  
  
public class Person  
{  
    public string Name { get; private set; }  
    public int Age { get; private set; }  
  
    public Person(string name, int age)  
    {  
        Name = name;  
        Age = age;  
    }  
  
    // Copy constructor CA1062 fires because other is dereferenced  
    // without being checked for null  
    public Person(Person other)  
        : this(other.Name, other.Age)  
    {  
    }  
}  
  
```  
  
## 使用例  
 次の `Person` の修正例では、コピー コンストラクターに渡される `other` オブジェクトが null であるかどうかが、`PassThroughNonNull` メソッドによって最初に確認されます。  
  
```  
public class Person  
{  
    public string Name { get; private set; }  
    public int Age { get; private set; }  
  
    public Person(string name, int age)  
    {  
        Name = name;  
        Age = age;  
    }  
  
    // Copy constructor  
    public Person(Person other)  
        : this(PassThroughNonNull(other).Name,   
          PassThroughNonNull(other).Age)  
    {   
    }  
  
    // Null check method  
    private static Person PassThroughNonNull(Person person)  
    {  
        if (person == null)  
            throw new ArgumentNullException("person");  
        return person;  
    }  
}  
  
```