---
title: "&#39;&lt;procedure1&gt;&#39; と &#39;&lt;procedure2&gt;&#39; は、パラメータが &#39;ByRef&#39; と &#39;ByVal&#39; で宣言されていることしか異ならないため、互いにオーバーロードすることはできません | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42003"
  - "bc42003"
helpviewer_keywords: 
  - "BC42003"
ms.assetid: f058f1e0-64d2-4497-85fc-a58e16b0d805
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;procedure1&gt;&#39; と &#39;&lt;procedure2&gt;&#39; は、パラメータが &#39;ByRef&#39; と &#39;ByVal&#39; で宣言されていることしか異ならないため、互いにオーバーロードすることはできません
'\<procedure1\>' と '\<procedure2\>' は、パラメータが 'ByRef' と 'ByVal' で宣言されていることしか異ならないため、互いにオーバーロードすることはできません。 シャドウとみなされます。  
  
 2 つのプロシージャ宣言で同じ名前と引数リストが指定されており、唯一の相違点は 1 つ以上の引数で `ByRef` または `ByVal` が指定されていることです。 オーバーロードされるバージョンのプロシージャは、引数の数、順序、またはデータ型が互いに異なっている必要があります。  
  
 このメッセージは警告です。`Shadows` は、既定で指定されています。 警告を非表示にする方法や、警告をエラーとして扱う方法については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC42003  
  
### このエラーを解決するには  
  
-   オーバーロードされるバージョンのプロシージャ セットを作成する場合は、各バージョンの引数の数、順序、またはデータ型を異なるものにします。 また、`Overloads` キーワードを各宣言に追加します。  
  
-   プロシージャをオーバーロードしない場合は、いずれかの宣言のプロシージャ名を変更します。  
  
## 参照  
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)