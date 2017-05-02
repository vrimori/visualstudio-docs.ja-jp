---
title: "デバッグ定数 | Microsoft Docs"
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
ms.assetid: 76b572ee-bad0-404e-9fd4-841c9af35642
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# デバッグ定数
DEBUG 定数は、`Debug` オブジェクトのプロパティになっている定数値を返します。  
  
## Debug オブジェクトの定数  
 [Debug オブジェクト](../../javascript/reference/debug-object-javascript.md)のプロパティになっている定数値を次の表に示します。  
  
|定数|説明|値|  
|--------|--------|-------|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`|同期作業項目は、非同期操作が実行するコールバックまたは継続を割り当てました。|0|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`|同期作業項目は、非同期の結合操作の一部を満たしました。|1|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`|同期作業項目は、非同期の選択操作を満たしました。|2|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`|同期作業項目は取り消されました。|3|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`|同期作業項目は、非同期操作でエラーが発生しました。|4|  
|`Debug.MS_ASYNC_OP_STATUS_SUCCESS`|非同期操作は正常に終了しました。|1|  
|`Debug.MS_ASYNC_OP_STATUS_CANCELED`|非同期操作は取り消されました。|2|  
|`Debug.MS_ASYNC_OP_STATUS_ERROR`|非同期操作でエラーが発生しました。|3|  
  
## 要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 参照  
 [Debug.msTraceAsyncOperationCompleted 関数](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md)   
 [Debug.msUpdateAsyncCallbackRelation 関数](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md)