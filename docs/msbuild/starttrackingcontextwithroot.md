---
title: "StartTrackingContextWithRoot | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "StartTrackingContextWithRoot"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StartTrackingContextWithRoot"
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# StartTrackingContextWithRoot
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ルート マーカーを指定する応答ファイルを使用して、追跡コンテキストを開始します。  
  
## 構文  
  
```  
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);  
```  
  
#### パラメーター  
 \[入力\] `intermediateDirectory`  
 追跡ログを格納するディレクトリ。  
  
 \[入力\] `taskName`  
 追跡コンテキストを識別します。  この名前を使用してログ ファイル名が作成されます。  
  
 \[入力\] `rootMarkerResponseFile`  
 ルート マーカーを格納している応答ファイルのパス名。  このルート名を使用して、コンテキストのすべての追跡がグループ化されます。  
  
## 戻り値  
 追跡コンテキストが作成された場合、[SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) ビットが設定された [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True)。  
  
## 必要条件  
 **ヘッダー:** FileTracker.h  
  
## 参照  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)