---
title: "属性 &#39;System.Runtime.InteropServices.DefaultCharSetAttribute&#39; はこのバージョンではサポートされていません | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32510"
  - "vbc32510"
helpviewer_keywords: 
  - "BC32510"
ms.assetid: e2eec233-6e0b-4f2f-a801-b0274e579c0e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 属性 &#39;System.Runtime.InteropServices.DefaultCharSetAttribute&#39; はこのバージョンではサポートされていません
<xref:System.Runtime.InteropServices.DefaultCharSetAttribute?displayProperty=fullName> 属性では、マーシャリングされた文字列で使用する文字セットを指定できます。 この値には、<xref:System.Runtime.InteropServices.CharSet?displayProperty=fullName> 列挙体のメンバーを指定します。  
  
 現在のバージョンの [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では、この属性をサポートしていません。 将来のバージョンではサポートされる可能性があります。  
  
 **エラー ID:** BC32510  
  
### このエラーを解決するには  
  
-   各 [Declare Statement](/dotnet/visual-basic/language-reference/statements/declare-statement) を使用して、宣言している外部プロシージャに対して文字セットを指定します。 次に例を示します。  
  
    ```  
    Ansi Declare Function GetUserName Lib "advapi32.dll" _ (ByVal lpBuffer As String, ByRef nSize As Integer) As Integer Unicode Declare Sub externalProc Lib "projectlib.dll" _ (ByVal arg As Double)  
    ```  
  
     `Declare` ステートメントで文字セットを指定しなかった場合は、既定で ANSI になります。  
  
## 参照  
 <xref:System.Runtime.InteropServices.DefaultCharSetAttribute>   
 <xref:System.Runtime.InteropServices.CharSet>   
 [NOT IN BUILD: Visual Basic における属性](http://msdn.microsoft.com/ja-jp/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [Declare Statement](/dotnet/visual-basic/language-reference/statements/declare-statement)