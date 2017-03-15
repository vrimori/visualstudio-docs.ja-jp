---
title: "DA0013: String.Split/String.Substring が頻繁に使用されています | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.13"
  - "vs.performance.rules.DAAvoidStringSubstr"
  - "vs.performance.DA0013"
  - "vs.performance.rules.DA0013"
helpviewer_keywords: 
  - "vs.performance.13"
  - "vs.performance.rules.DA0013"
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0013: String.Split/String.Substring が頻繁に使用されています
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0013|  
|分類|.NET Framework の使用ガイダンス|  
|プロファイル方法|サンプリング|  
|メッセージ|String.Split 関数と String.Substring 関数の使用回数を減らすことを検討してください。|  
|規則の種類|警告|  
  
## 原因  
 System.String.Split メソッドまたは System.String.Substring メソッドの呼び出しがプロファイル データの大きな割合を占めています。  文字列内に部分文字列が存在することをテストする場合は、System.String.IndexOf または System.String.IndexOfAny を使用することを検討してください。  
  
## 規則の説明  
 Split メソッドは、String オブジェクトを操作し、元の文字列の部分文字列を含む文字列の新しい配列を返します。  関数は、返された配列オブジェクトにメモリを割り当て、検出された配列要素ごとに新しい String オブジェクトを割り当てます。  同様に、Substr メソッドは String オブジェクトを操作し、要求された部分文字列と等しい新しい文字列を返します。  
  
 メモリの割り当ての管理がアプリケーションにおいて重要な場合、String.Split メソッドと String.Substr メソッドの代替手段を使用することを検討してください。  たとえば、IndexOf メソッドまたは IndexOfAny メソッドを使用すると、String クラスの新しいインスタンスを作成しなくても、文字列内の特定の部分文字列を見つけることができます。  
  
## 警告の調査方法  
 \[エラー一覧\] ウィンドウに表示されたメッセージをダブルクリックして、サンプリング プロファイル データの[関数の詳細ビュー](../profiling/function-details-view.md)に移動します。  呼び出し関数を調べ、System.String.Split メソッドまたは System.String.Substr メソッドを最も頻繁に使用するプログラムのセクションを見つけます。  可能な場合は、IndexOf メソッドまたは IndexOfAny メソッドを使用して、String クラスの新しいインスタンスを作成せずに、文字列内の特定の部分文字列を見つけます。