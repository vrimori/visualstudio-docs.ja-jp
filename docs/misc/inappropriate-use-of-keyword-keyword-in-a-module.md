---
title: "モジュールでの &lt;keyword&gt; キーワードの使い方が正しくありません | Microsoft Docs"
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
  - "vbc42028"
  - "BC42028"
helpviewer_keywords: 
  - "BC42028"
ms.assetid: a9bc1e9d-ba2c-4a71-b147-0fb66f670316
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# モジュールでの &lt;keyword&gt; キーワードの使い方が正しくありません
モジュールはインスタンスを持たず、継承をサポートしたり、インターフェイスを実装したりしません。 そのため、次のキーワードはモジュールの宣言に適用されません。  
  
-   [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)  
  
-   [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)  
  
-   [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)  
  
-   [Private](/dotnet/visual-basic/language-reference/modifiers/private)  
  
-   [Protected](/dotnet/visual-basic/language-reference/modifiers/protected)  
  
-   [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)  
  
-   [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)  
  
-   [Static](/dotnet/visual-basic/language-reference/modifiers/static)  
  
 [Module Statement](/dotnet/visual-basic/language-reference/statements/module-statement) でサポートされるキーワードは、[Public](/dotnet/visual-basic/language-reference/modifiers/public) と [Friend](/dotnet/visual-basic/language-reference/modifiers/friend) のみです。  
  
 また、[Implements](/dotnet/visual-basic/language-reference/statements/implements-clause) ステートメントまたは [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement) をモジュールのステートメント ブロックで使用することはできません。  
  
 既定では、このメッセージは警告です。 警告を表示しない方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC42028  
  
### このエラーを解決するには  
  
-   このプログラミング要素をモジュールにする場合は、その宣言内で `Public` キーワードまたは `Friend` キーワードのみを使用します。 モジュールのアクセス レベルを指定しない場合、既定では `Friend` が使用されます。  
  
-   このプログラミング要素のインスタンスを作成する場合は、クラスとして宣言します。 そうすると、クラス宣言に適用されるキーワードを使用できます。  
  
## 参照  
 [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement)