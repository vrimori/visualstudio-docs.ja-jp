---
title: "DA0006: 値の型で Equals() をオーバーライドしてください | Microsoft Docs"
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
  - "vs.performance.rules.DAOverrideEquals"
  - "vs.performance.6"
  - "vs.performance.DA0006"
  - "vs.performance.rules.DA0006"
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0006: 値の型で Equals() をオーバーライドしてください
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0006|  
|分類|.NET Framework の使用|  
|プロファイル方法|サンプリング|  
|メッセージ|値の型で Equals と等値演算子をオーバーライドしてください。|  
|メッセージの種類|警告|  
  
## 原因  
 Equals メソッドまたはパブリックの値型の等値演算子の呼び出しがプロファイル データの大きな割合を占めています。  より効率的な方法を実装することを検討してください。  
  
## 規則の説明  
 値型の場合、Equals を継承した実装が <xref:System.Reflection> ライブラリを使用して、型のすべてのフィールドの内容を比較します。  Reflection は計算コストが高いため、場合によってはすべてのフィールドで等値性を比較する必要はありません。  ユーザーがインスタンスの比較または並べ替えを行うことや、ハッシュ テーブル キーとしてインスタンスを使用することが予想される場合には、値型に Equals を実装する必要があります。  また、プログラム言語で演算子のオーバーロードをサポートしている場合、等値演算子と非等値演算子を実装する必要もあります。  
  
 この方法の詳細については Equals と等値演算子のオーバーライドする参照します [実装する際のガイドライン Equals と等値演算子 \(\=\=\) を](http://go.microsoft.com/fwlink/?LinkId=177818)。  
  
## 警告の調査方法  
 Equals と等値演算子の実装例については、コード分析規則「[CA1815: equals および operator equals を値型でオーバーライドします](../Topic/CA1815:%20Override%20equals%20and%20operator%20equals%20on%20value%20types.md)」を参照してください。