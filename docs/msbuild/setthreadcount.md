---
title: "SetThreadCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "SetThreadCount"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "SetThreadCount"
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# SetThreadCount
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

グローバルなスレッドの数を設定し、その数を現在のスレッドに割り当てます。  
  
## 構文  
  
```  
HRESULT WINAPI SetThreadCount(int threadCount);  
```  
  
#### パラメーター  
 \[入力\] `threadCount`  
 使用するスレッドの数。  
  
## 戻り値  
 スレッド数が更新された場合、[SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) ビットが設定された [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True)。  
  
## 必要条件  
 **ヘッダー:** FileTracker.h