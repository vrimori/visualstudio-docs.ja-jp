---
title: "WriteAllTLogs | Microsoft Docs"
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
  - "WriteAllTLogs"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "WriteAllTLogs"
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# WriteAllTLogs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

すべてのスレッドおよびコンテキストに対する追跡ログを書き込みます。  
  
## 構文  
  
```  
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### パラメーター  
 \[入力\] `intermediateDirectory`  
 追跡ログを格納するディレクトリ。  
  
 \[入力\] `tlogRootName`  
 ログ ファイル名のルート名。  
  
## 戻り値  
 追跡コンテキストが作成された場合、[SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) ビットが設定された [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True)。  
  
## 必要条件  
 **ヘッダー:** FileTracker.h  
  
## 参照  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)