---
title: "CA1024: 適切な場所にプロパティを使用します | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UsePropertiesWhereAppropriate"
  - "CA1024"
helpviewer_keywords: 
  - "CA1024"
  - "UsePropertiesWhereAppropriate"
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1024: 適切な場所にプロパティを使用します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UsePropertiesWhereAppropriate|  
|CheckId|CA1024|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリック メソッドまたはプロテクト メソッドに、`Get` で始まる名前が付けられ、パラメーターは使用されていません。また、配列ではない値を返します。  
  
## 規則の説明  
 ほとんどの場合、プロパティはデータを表し、メソッドはアクションを実行します。  プロパティにはフィールドと同様にアクセスできるため、使用が簡単です。  次のいずれかの条件に該当する場合は、メソッドをプロパティに変更できる可能性があります。  
  
-   引数を受け取らず、オブジェクトのステータス情報を返す場合。  
  
-   オブジェクトの状態の一部を設定する単一の引数を受け取る場合。  
  
 プロパティは、フィールドと同様に動作します。メソッドで同様に動作できない場合、プロパティに変更しないでください。  次のような場合、プロパティよりもメソッドの方が適しています。  
  
-   メソッドで時間のかかる操作を実行する場合。  メソッドは、フィールド値の設定または取得に必要な時間よりも、明らかに長くかかります。  
  
-   メソッドで変換を実行する場合。  フィールドへのアクセスでは、格納データの変換されたバージョンは返されません。  
  
-   Get メソッドに明らかな副作用がある場合。  フィールド値の取得には副作用はありません。  
  
-   実行順序が重要となる場合。  フィールド値の設定は、発生した他の操作に依存しません。  
  
-   メソッドを 2 回続けて呼び出した場合に、異なる結果が生じるとき。  
  
-   メソッドが静的でも、呼び出し元によって変更できるオブジェクトを返す場合。  フィールド値の取得の場合、呼び出し元は、フィールドに格納されているデータを変更できません。  
  
-   メソッドが配列を返す場合。  
  
## 違反の修正方法  
 この規則違反を修正するには、メソッドをプロパティに変更します。  
  
## 警告を抑制する状況  
 メソッドが上記で列挙した基準のいずれかに適合する場合、この規則からの警告を抑制します。  
  
## デバッガーでのプロパティの展開の制御  
 プログラマがプロパティの使用を避ける理由の 1 つは、デバッガーがプロパティを自動展開するのを好まないためです。  たとえば、プロパティが大きなオブジェクトの割り当てや P\/Invoke の呼び出しに関連していても、実際には明らかな影響を及ぼさない場合があります。  
  
 <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName> を適用することで、デバッガーがプロパティを自動展開しないようにすることができます。  次の例では、この属性がインスタンス プロパティに適用されています。  
  
```vb  
Imports System   
Imports System.Diagnostics   
  
Namespace Microsoft.Samples   
  
    Public Class TestClass   
  
        ' [...]   
  
        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _   
        Public ReadOnly Property LargeObject() As LargeObject   
            Get   
                ' Allocate large object   
                ' [...]   
            End Get   
        End Property   
  
    End Class   
  
End Namespace  
```  
  
```c#  
  
        using System;   
using System.Diagnostics;   
  
namespace Microsoft.Samples   
{   
    public class TestClass   
    {   
        // [...]   
  
        [DebuggerBrowsable(DebuggerBrowsableState.Never)]   
        public LargeObject LargeObject   
        {   
            get   
            {   
                // Allocate large object   
                // [...]   
  
        }  
    }  
}  
```  
  
## 使用例  
 次の例には、プロパティに変換する方がよいメソッドと、フィールドのように動作しないため変換しない方がよいメソッドがいくつか含まれています。  
  
 [!code-cs[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]