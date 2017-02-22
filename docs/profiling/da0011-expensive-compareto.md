---
title: "DA0011: CompareTo の負荷が高くなっています | Microsoft Docs"
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
  - "vs.performance.DA0011"
  - "vs.performance.rules.DAExpensiveCompareTo"
  - "vs.performance.11"
  - "vs.performance.rules.DA0011"
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0011: CompareTo の負荷が高くなっています
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0011|  
|分類|.NET Framework の使用|  
|プロファイル方法|サンプリング<br /><br /> .NET メモリ|  
|メッセージ|CompareTo 関数の負荷を抑える必要があります。これらの関数でメモリを割り当てることはできません。  可能な場合は、CompareTo 関数の複雑さを軽減してください。|  
|規則の種類|警告|  
  
## 原因  
 型の CompareTo メソッドの負荷が高くなっているか、このメソッドがメモリを割り当てています。  
  
## 規則の説明  
 CompareTo メソッドは効率的である必要があり、メモリを割り当てることはできません。  
  
## 違反の修正方法  
 ComepareTo メソッドの複雑さを軽減します。