---
title: "JsDisableRuntimeExecution 関数 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsDisableRuntimeExecution
helpviewer_keywords: JsDisableRuntimeExecution function
ms.assetid: 4bd4670a-a9da-4f8c-b3fd-1fd366d915c3
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f44545f7c81344a2d22f0083087f77ac8074278c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="jsdisableruntimeexecution-function"></a>JsDisableRuntimeExecution 関数
スクリプトの実行を中断し、ランタイム内のすべての実行スクリプトを終了します。  
  
## <a name="syntax"></a>構文  
  
```  
STDAPI_(JsErrorCode) JsDisableRuntimeExecution(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `runtime`  
 中断するランタイム。  
  
## <a name="return-value"></a>戻り値  
 操作が成功した場合はコード `JsNoError` 、操作が失敗した場合はエラー コード。  
  
## <a name="remarks"></a>コメント  
 中断されたランタイムの呼び出しは、`JsEnableRuntimeExecution` を呼び出すまで失敗します。  
  
 この API は、ランタイムがアクティブなスレッドで呼び出す必要はありません。 ランタイムは中断状態に設定されますが、スクリプトの実行は直ちに中断できません。実行中のスクリプトは、キャッチ不可能な例外により、できる限り早急に終了します。  
  
 既に中断されているランタイムで実行を中断しても何も行われません。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)