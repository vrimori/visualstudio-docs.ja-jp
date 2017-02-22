---
title: "ResumeTracking | Microsoft Docs"
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
  - "ResumeTracking"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "ResumeTracking"
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ResumeTracking
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

現在のコンテキストで追跡を再開します。  
  
## 構文  
  
```  
HRESULT WINAPI ResumeTracking();  
```  
  
## 戻り値  
 追跡が再開された場合、[SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) ビットが設定された [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True)。  コンテキストを使用できなかったために追跡を再開できない場合は、[E\_FAIL](assetId:///E_FAIL?qualifyHint=False&autoUpgrade=True) が返されます。  
  
## 必要条件  
 **ヘッダー:** FileTracker.h  
  
## 参照  
 [SuspendTracking](../msbuild/suspendtracking.md)