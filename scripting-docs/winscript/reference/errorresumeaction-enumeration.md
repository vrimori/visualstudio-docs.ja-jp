---
title: "ERRORRESUMEACTION 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ERRORRESUMEACTION
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ERRORRESUMEACTION 列挙型"
ms.assetid: a68293c8-056b-439f-83e7-69e4a38f4976
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ERRORRESUMEACTION 列挙型
ランタイム エラーから続行する方法について説明します。  
  
## 構文  
  
```  
typedef enum tagERRORRESUMEACTION {  
   ERRORRESUMEACTION_ReexecuteErrorStatement,  
   ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller,  
   ERRORRESUMEACTION_SkipErrorStatement,  
} ERRORRESUMEACTION;  
```  
  
## メンバー  
  
|メンバー|説明|  
|----------|--------|  
|ERRORRESUMEACTION\_ReexecuteErrorStatement|エラーを生成するステートメントを再実行します。|  
|ERRORRESUMEACTION\_AbortCallAndReturnErrorToCaller|言語のエンジンがエラーを処理できます。|  
|ERRORRESUMEACTION\_SkipErrorStatement|エラーを生成したステートメントに続くコードの実行を再開します。|  
  
## 参照  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)