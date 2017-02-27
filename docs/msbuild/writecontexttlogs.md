---
title: "WriteContextTLogs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "WriteContextTLogs"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "WriteContextTLogs"
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# WriteContextTLogs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

現在のコンテキストに対するログ ファイルを書き込みます。  
  
## 構文  
  
```  
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
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
 [WriteAllTLogs](../msbuild/writealltlogs.md)