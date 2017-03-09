---
title: "基底クラスに、&lt;type&gt; &#39;&lt;typename&gt;&#39; と同じオーバーロード可能なメソッドが存在します | Microsoft Docs"
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
  - "vbc40005"
  - "bc40005"
helpviewer_keywords: 
  - "BC40005"
ms.assetid: 1dadda7f-1d26-4ae8-a668-9f69d55ceb50
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 基底クラスに、&lt;type&gt; &#39;&lt;typename&gt;&#39; と同じオーバーロード可能なメソッドが存在します
基底クラスに、\<type\> '\<typename\>' と同じオーバーロード可能なメソッドが存在します。 ベース メソッドをオーバーライドするには、このメソッドは 'Overrides' に宣言されている必要があります。  
  
 プログラミング要素が、基底クラスで定義されたオーバーライド可能なプロシージャまたはプロパティと同じ名前で宣言されています。 この場合、このクラスの要素は、基底クラス要素をシャドウする必要があります。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC40005  
  
### このエラーを解決するには  
  
-   基本のプロシージャをオーバーライドする場合は、`Overrides` キーワードを宣言に追加します。  
  
-   基本のプロシージャをシャドウする場合は、`Shadows` キーワードを宣言に追加します。  
  
-   オーバーライドまたはシャドウをどちらも行わない場合は、宣言される要素の名前を変更します。  
  
## 参照  
 [ビルド内にありません: プロパティとメソッドのオーバーライド](http://msdn.microsoft.com/ja-jp/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Shadowing in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)   
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)