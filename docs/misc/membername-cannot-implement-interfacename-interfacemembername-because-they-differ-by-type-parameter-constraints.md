---
title: "型パラメーター制約が異なるため、&#39;&lt;membername&gt;&#39; は &#39;&lt;interfacename&gt;.&lt;interfacemembername&gt;&#39; を実装できません | Microsoft Docs"
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
  - "vbc32078"
  - "BC32078"
helpviewer_keywords: 
  - "BC32078"
ms.assetid: 2c971345-edb4-491e-9202-8eb8286b66f8
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型パラメーター制約が異なるため、&#39;&lt;membername&gt;&#39; は &#39;&lt;interfacename&gt;.&lt;interfacemembername&gt;&#39; を実装できません
汎用イベント、プロパティ、またはプロシージャが、インターフェイスで定義されている類似したメンバーの実装を試みていますが、型パラメーターとは異なる制約リストがあります。  
  
 インターフェイス メンバーを実装するには、実装しているメンバーがインターフェイス メンバーの完全な署名だけでなく、各パラメーターの引渡し方法を一致させなければなりません。  
  
 汎用インターフェイスのメンバーを実装するには、実装しているメンバーがさらに型パラメーターの数と 1 つずつの制約一覧を一致させなければなりません。  
  
 インターフェイスの実装の詳細については、「[ビルド内にありません: キーワードの実装とステートメントの実装](http://msdn.microsoft.com/ja-jp/b96560f7-6413-480f-a1e2-f80253bab5be)」を参照してください。  
  
 **エラー ID:** BC32078  
  
### このエラーを解決するには  
  
-   インターフェイスのメンバーを実装する場合は、インターフェイスのメンバーと完全に一致するよう型パラメーター制約を変更します。  
  
-   型パラメーターの制約をそのままにしておく必要がある場合、この宣言でインターフェイス メンバーを実装することはできません。 宣言から [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause) キーワードを削除します。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [ビルド内にありません: Visual Basic でのインターフェイスの実装例](http://msdn.microsoft.com/ja-jp/50bf2a30-73b6-4126-a921-075fd6eec278)