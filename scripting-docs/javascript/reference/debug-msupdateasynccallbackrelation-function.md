---
title: "Debug.msUpdateAsyncCallbackRelation 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ee6a1efc-375c-4ce8-a4e8-8896ee29f849
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Debug.msUpdateAsyncCallbackRelation 関数
同期作業項目と関連付けられた非同期操作の間のリレーションシップのステータスを更新します。  
  
## 構文  
  
```  
Debug.msUpdateAsyncCallbackRelation(relatedAsyncOperationId, relationType)  
```  
  
#### パラメーター  
 `relatedAsyncOperationId`  
 必ず指定します。  非同期操作に関連付けられた ID。  
  
 `relationType`  
 省略可能です。  リレーションシップのステータスを指定する値。  
  
## 解説  
 同期作業項目は、通常、非同期操作のコールバック関数です。  この関数は、非同期操作が中止される場合、結合操作を使用する場合、または他のシナリオで、呼び出される場合もあります。  
  
 `relationType` は次のような値となります。  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`  
  
 詳細については、「[\/DEBUG 定数](../../javascript/reference/debug-constants.md)」を参照してください。  
  
> [!NOTE]
>  デバッグ ツールによっては、この関数がデバッガーに送信する情報を表示しません。  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]