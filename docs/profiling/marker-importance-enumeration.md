---
title: "marker_importance 列挙型 | Microsoft Docs"
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
  - "cvmarkersobj/Concurrency::diagnostic::marker_importance"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_importance 列挙型"
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# marker_importance 列挙型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

同時実行ビジュアライザー マーカーの重要度レベルを表します。  
  
## 構文  
  
```  
enum marker_importance;  
```  
  
## メンバー  
  
### 値  
  
|名前|説明|  
|--------|--------|  
|`critical_importance`|マーカーがきわめて重要であることを指定します。|  
|`high_importance`|マーカーの重要度が高いことを指定します。|  
|`low_importance`|マーカーの重要度が低いことを指定します。|  
|`normal_importance`|マーカーの重要度が普通であることを指定します。|  
  
## 必要条件  
 **ヘッダー:** cvmarkersobj.h  
  
 **名前空間:** Concurrency::diagnostic  
  
## 参照  
 [diagnostic 名前空間](../profiling/diagnostic-namespace.md)