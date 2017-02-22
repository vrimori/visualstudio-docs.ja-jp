---
title: "StopTrackingAndCleanup | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "StopTrackingAndCleanup"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StopTrackingAndCleanup"
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# StopTrackingAndCleanup
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

すべての追跡を停止し、追跡セッションで使用されているメモリを解放します。  
  
## 構文  
  
```  
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## 戻り値  
 追跡が停止された場合、[SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) ビットが設定された [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) を返します。  
  
## 必要条件  
 **ヘッダー:** FileTracker.h  
  
## 参照  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)