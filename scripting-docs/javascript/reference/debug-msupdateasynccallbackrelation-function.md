---
title: "Debug.msUpdateAsyncCallbackRelation 関数 |Microsoft ドキュメント"
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
ms.assetid: ee6a1efc-375c-4ce8-a4e8-8896ee29f849
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c47ed7f6313646dddf86dd766d7f1027b2d38ad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="debugmsupdateasynccallbackrelation-function"></a>Debug.msUpdateAsyncCallbackRelation 関数
同期作業項目と関連付けられた非同期操作の間のリレーションシップのステータスを更新します。  
  
## <a name="syntax"></a>構文  
  
```  
Debug.msUpdateAsyncCallbackRelation(relatedAsyncOperationId, relationType)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `relatedAsyncOperationId`  
 必須です。 非同期操作に関連付けられた ID。  
  
 `relationType`  
 省略可能です。 リレーションシップのステータスを指定する値。  
  
## <a name="remarks"></a>コメント  
 同期作業項目は、通常、非同期操作のコールバック関数です。 この関数は、非同期操作が中止される場合、結合操作を使用する場合、または他のシナリオで、呼び出される場合もあります。  
  
 `relationType` は次のような値となります。  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`  
  
 詳細については、次を参照してください。[デバッグ定数](../../javascript/reference/debug-constants.md)です。  
  
> [!NOTE]
>  デバッグ ツールによっては、この関数がデバッガーに送信する情報を表示しません。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]