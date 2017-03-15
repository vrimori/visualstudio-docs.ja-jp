---
title: "&#39;ParamArray&#39; を拡張メソッドの最初のパラメーターに適用できません。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36554"
  - "bc36554"
helpviewer_keywords: 
  - "BC36554"
ms.assetid: 0778a854-246f-4c2b-943d-ea8883b3aa6f
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ParamArray&#39; を拡張メソッドの最初のパラメーターに適用できません。
'ParamArray' を拡張メソッドの最初のパラメーターに適用できません。 最初のパラメーターは、拡張する型を指定します。  
  
 拡張メソッドの最初のパラメーターでは、そのメソッドが拡張するデータ型を指定します。 そのため、最初のパラメーターは必須であり、省略可能にすることはできません。 パラメーター配列は、自動的に省略可能であるため、拡張メソッドの最初の引数として有効ではありません。  
  
> [!NOTE]
>  メソッドが実行されると、そのメソッドを呼び出す拡張データ型のインスタンスが、メソッドの最初のパラメーターの引数になります。 たとえば、`greeting.Print()` のインスタンス `greeting` は、拡張メソッド `Public Sub Print (ByVal str As String)` の最初のパラメーター `str` の引数です。  
  
 **エラー ID:** BC36554  
  
### このエラーを解決するには  
  
-   パラメーター配列で拡張するデータ型を指定しない場合は、その型を指定する新しい最初のパラメーターを追加します。  
  
    ```  
    <Extension()> Public Sub AddTo(ByRef str As String, ByVal ParamArray addOns() As String) ' Concatenate the strings in addOns to str. End Sub  
    ```  
  
-   パラメーター配列で拡張するデータ型を指定する場合は、パラメーター配列の代わりに、引数を必要とする通常の配列に変更することを検討してください。 通常の配列は、拡張できます。  
  
    ```  
    <Extension()> Public Function Sum(ByVal ints() As Integer) As Integer Dim total As Integer = 0 For Each i As Integer In ints total = total + i Next i Return total End Function  
    ```  
  
## 参照  
 [拡張メソッド](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Parameter Arrays](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)   
 [Optional Parameters](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)