---
title: "&#39;implements &lt;derivedinterfacename&gt;&#39; からの &#39;&lt;baseinterfacename&gt;.&lt;membername&gt;&#39; は、基底クラス &#39;&lt;baseclassname&gt;&#39; によって既に実装されています。 &lt;type&gt; の再実装と見なされます。 | Microsoft Docs"
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
  - "bc42014"
  - "vbc42014"
helpviewer_keywords: 
  - "BC42014"
ms.assetid: 95fff622-5d54-4ec8-90f0-477de1d58687
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;implements &lt;derivedinterfacename&gt;&#39; からの &#39;&lt;baseinterfacename&gt;.&lt;membername&gt;&#39; は、基底クラス &#39;&lt;baseclassname&gt;&#39; によって既に実装されています。 &lt;type&gt; の再実装と見なされます。
派生クラスのプロパティ、プロシージャ、またはイベントで `Implements` 句を使用し、基底クラスの基底インターフェイス上に既に実装されている派生インターフェイス メンバーを指定します。  
  
 実装されているメンバーは、基底インターフェイスによって定義され、派生インターフェイスによって継承されます。 基底クラスには基底インターフェイスが直接実装されます。 派生クラスでは、派生インターフェイスが実装され、ほとんどの場合、基底クラスでそのメンバーが既に実装されているとは認識されません。  
  
 派生クラスでは、その基底クラスによって実装されているインターフェイス メンバーを再実装できます。 このことは、基底クラスの実装をオーバーライドすることとは異なります。 詳細については、「[Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)」を参照してください。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC42014  
  
### このエラーを解決するには  
  
-   インターフェイス メンバーを再実装する場合は、操作を行う必要はありません。 派生クラスのコードでは、[MyBase \- delete](http://msdn.microsoft.com/ja-jp/52491d06-6451-4f6f-9aa6-8fab59bbc2b9) キーワードを使用して基底クラスの実装にアクセスしない限り、再実装されたメンバーにアクセスします。  
  
-   インターフェイス メンバーを再実装しない場合は、プロパティ、プロシージャ、またはイベント宣言から、`Implements` 句を削除します。  
  
## 参照  
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [ビルド内にありません: Implements キーワードおよび Implements ステートメント](http://msdn.microsoft.com/ja-jp/b96560f7-6413-480f-a1e2-f80253bab5be)