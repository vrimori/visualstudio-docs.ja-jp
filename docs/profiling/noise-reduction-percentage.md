---
title: "不要項目の非表示の割合 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.filter"
helpviewer_keywords: 
  - "同時実行ビジュアライザー, 不要項目の非表示の割合"
ms.assetid: 1c10cd4c-2fdd-48c9-b562-a334b3b2df6c
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 不要項目の非表示の割合
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

既定では、不要項目の非表示の割合の設定値は 2 です。  この設定値以上の包括時間の割合を持つエントリだけが、コール ツリーに表示されます。  この設定を変更することによって、コール ツリーに表示されるエントリの数を制御できます。  たとえば、設定値を 10 に変更すると、10% 以上の包括時間を持つエントリだけが、コール ツリーに表示されます。  この設定値を大きくすると、プロセスのパフォーマンスに対する影響度が高いエントリに集中することができます。