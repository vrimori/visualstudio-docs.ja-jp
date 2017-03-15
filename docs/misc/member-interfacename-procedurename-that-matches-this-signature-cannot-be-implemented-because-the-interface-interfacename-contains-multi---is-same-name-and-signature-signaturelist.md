---
title: "このシグネチャに一致するメンバー &#39;&lt;interfacename&gt;.&lt;procedurename&gt;&#39; を実装することはできません。インターフェイス &#39;&lt;interfacename&gt;&#39; がこの同じ名前とシグネチャ &lt;signaturelist&gt; の複数のメンバーを含むためです。 | Microsoft Docs"
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
  - "vbc30937"
  - "bc30937"
helpviewer_keywords: 
  - "BC30937"
ms.assetid: e917d85e-95e0-431a-9d09-39ce5d4fc894
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# このシグネチャに一致するメンバー &#39;&lt;interfacename&gt;.&lt;procedurename&gt;&#39; を実装することはできません。インターフェイス &#39;&lt;interfacename&gt;&#39; がこの同じ名前とシグネチャ &lt;signaturelist&gt; の複数のメンバーを含むためです。
プロシージャまたはプロパティが、実装されたインターフェイスの中で定義されているプロシージャまたはプロパティを実装しようとしましたが、コンパイラは、同じ名前とシグネチャを持つインターフェイス プロシージャまたはプロパティを複数見つけました。  
  
 このエラーは、次のスケルトン宣言に示すように、ジェネリック型が構築されている場合に発生することがあります。  
  
```  
Public Interface baseInterface(Of t) Sub doSomething(ByVal inputValue As String) Sub doSomething(ByVal inputValue As t) End Class Public Class implementingClass Implements baseInterface(Of String) Sub doSomething(ByVal inputValue As String) _ Implements baseInterface(Of String).doSomething End Sub End Class  
```  
  
 `implementingClass` は `String` を型パラメーター `t` に指定する `baseInterface` を実装するため、`implementingClass` に関する限り、`baseInterface` にある `doSomething` の 2 つのバージョンが同じシグネチャを持つことになります。 そのため、コンパイラはどちらのバージョンを実装するべきか判断できません。  
  
 **エラー ID:** BC30937  
  
### このエラーを解決するには  
  
-   メンバーのプロシージャまたはプロパティの 1 つまたは複数のシグネチャが同じにならないように、基底クラスに指定する 1 つ以上の型引数を変更します。  
  
     または  
  
-   この基底クラスを実装しないようにします。 個々のメンバーを実装する必要があるため、現在使用している一連の型引数でこれを実装することはできません。  
  
## 参照  
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [Implements Statement](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [ビルド内にありません: Implements キーワードおよび Implements ステートメント](http://msdn.microsoft.com/ja-jp/b96560f7-6413-480f-a1e2-f80253bab5be)