---
title: "ルート名前空間 &lt;namespacename&gt; は CLS に準拠していません | Microsoft Docs"
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
  - "bc40038"
  - "vbc40038"
helpviewer_keywords: 
  - "BC40038"
ms.assetid: ec850295-b2fe-4f19-b808-d22fe0aaa32d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ルート名前空間 &lt;namespacename&gt; は CLS に準拠していません
アセンブリが `<CLSCompliant(True)>` としてマークされているのに、ルート名前空間の名前がアンダースコア \(`_`\) で始まっています。  
  
 プログラミング要素には 1 つ以上のアンダースコアを含めることができますが、[言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) に準拠するためには、先頭をアンダースコアにしてはなりません。 「[Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)」を参照してください。  
  
 プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定して、準拠または非準拠を示します。 このパラメーターには既定値がありません。値を指定する必要があります。  
  
 <xref:System.CLSCompliantAttribute> を要素に適用しなかった場合は、非準拠と見なされます。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC40038  
  
### このエラーを解決するには  
  
-   CLS 準拠にする必要がある場合は、ルート名前空間の名前を変更し、アンダースコアで始まらないようにします。  
  
-   ルート名前空間の名前を変更できない場合は、アセンブリから <xref:System.CLSCompliantAttribute> を削除するか、アセンブリを `<CLSCompliant(False)>` としてマークします。  
  
## 参照  
 [Namespace Statement](/dotnet/visual-basic/language-reference/statements/namespace-statement)   
 [Visual Basic における名前空間](/dotnet/visual-basic/programming-guide/program-structure/namespaces)   
 [\/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace)   
 [NIB: 方法 : アプリケーションの名前空間を変更する \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/029d85c0-e173-4f7a-afba-a29f3aaf6ebf)   
 [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)   
 [Visual Basic Naming Conventions](/dotnet/visual-basic/programming-guide/program-structure/naming-conventions)   
 [\<PAVE OVER\> CLS 準拠コードの記述](http://msdn.microsoft.com/ja-jp/4c705105-69a2-4e5e-b24e-0633bc32c7f3)