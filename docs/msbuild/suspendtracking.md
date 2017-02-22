---
title: "SuspendTracking | Microsoft Docs"
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
  - "SuspendTracking"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "SuspendTracking"
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# SuspendTracking
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

現在のコンテキストで追跡を中断します。  
  
## 構文  
  
```  
HRESULT WINAPI SuspendTracking(void);  
```  
  
## 戻り値  
 追跡が中断された場合、[SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) ビットが設定された [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True)。  
  
## 必要条件  
 **ヘッダー:** FileTracker.h  
  
## 参照  
 [ResumeTracking](../msbuild/resumetracking.md)