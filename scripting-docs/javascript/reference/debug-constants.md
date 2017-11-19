---
title: "デバッグ定数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 76b572ee-bad0-404e-9fd4-841c9af35642
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2c50181dc9f40d8665d6caca407232231682d63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="debug-constants"></a>デバッグ定数
DEBUG 定数は、`Debug` オブジェクトのプロパティになっている定数値を返します。  
  
## <a name="debug-object-constants"></a>Debug オブジェクトの定数  
 次の表のプロパティを定数値、 [Debug オブジェクト](../../javascript/reference/debug-object-javascript.md)です。  
  
|定数|説明|値|  
|--------------|-----------------|-----------|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`|同期作業項目は、非同期操作が実行するコールバックまたは継続を割り当てました。|0|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`|同期作業項目は、非同期の結合操作の一部を満たしました。|1|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`|同期作業項目は、非同期の選択操作を満たしました。|2|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`|同期作業項目は取り消されました。|3|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`|同期作業項目は、非同期操作でエラーが発生しました。|4|  
|`Debug.MS_ASYNC_OP_STATUS_SUCCESS`|非同期操作は正常に終了しました。|1|  
|`Debug.MS_ASYNC_OP_STATUS_CANCELED`|非同期操作は取り消されました。|2|  
|`Debug.MS_ASYNC_OP_STATUS_ERROR`|非同期操作でエラーが発生しました。|3|  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Debug.msTraceAsyncOperationCompleted 関数](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md)   
 [Debug.msUpdateAsyncCallbackRelation 関数](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md)