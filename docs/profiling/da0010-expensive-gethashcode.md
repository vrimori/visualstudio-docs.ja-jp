---
title: "DA0010: GetHashCode の負荷が高くなっています | Microsoft Docs"
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
  - "vs.performance.rules.DAExpensiveGetHashCode"
  - "vs.performance.DA0010"
  - "vs.performance.rules.DA0010"
  - "vs.performance.10"
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0010: GetHashCode の負荷が高くなっています
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0010|  
|分類|.NET Framework の使用|  
|プロファイル方法|サンプリング<br /><br /> .NET メモリ|  
|メッセージ|GetHashCode 関数の負荷を抑える必要があります。これらの関数でメモリを割り当てることはできません。  可能な場合は、ハッシュ コード関数の複雑さを軽減してください。|  
|メッセージの種類|警告|  
  
## 原因  
 型の GetHashCode メソッドの呼び出しが、プロファイル データまたはメソッド割り当てメモリの大きな割合を占めています。  
  
## 規則の説明  
 ハッシュとは、大きなコレクションから特定の項目をすばやく見つけ出す手法のことです。  ハッシュ テーブルは非常に大きくなる可能性があり、高速のアクセス速度をサポートする必要があるため、ハッシュ テーブルの効率性は重要な要素になります。  この要件は、.NET Framework の GetHashCode メソッドでメモリの割り当てを行うべきではないということを意味しています。  メモリの割り当てを行うと、ガベージ コレクターの読み込みが増加し、割り当て要求の結果ガベージ コレクションが必要になった場合に、メソッドの潜在的な遅延が発生します。  
  
## 違反の修正方法  
 このメソッドの複雑さを軽減してください。