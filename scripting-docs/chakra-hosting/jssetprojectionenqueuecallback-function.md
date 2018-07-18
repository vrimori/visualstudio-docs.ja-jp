---
title: JsSetProjectionEnqueueCallback 関数 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c751ccef-20d2-4d41-9568-1c54adf47cdf
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8abdc575c5066ade4a700a0c88e09e3476a65366
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568982"
---
# <a name="jssetprojectionenqueuecallback-function"></a>JsSetProjectionEnqueueCallback 関数
呼び出し元の必要なスレッドに対して、射影の完了を呼び出すのに使用するコールバックを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
STDAPI_(JsErrorCode) JsSetProjectionEnqueueCallback(  
   _In_ JsProjectionEnqueueCallback projectionEnqueueCallback,  
   _In_opt_ void *projectionEnqueueContext);  
  
```  
  
#### <a name="parameters"></a>パラメーター  
 `projectionEnqueueContext`  
 バックグラウンド スレッドで射影の完了が発生するときに呼び出されるコールバック。  
  
 `callbackState`  
 `projectionEnqueueContext` に提供されるアプリケーション コンテキスト。  
  
## <a name="return-value"></a>戻り値  
 操作が成功した場合はコード `JsNoError` 、操作が失敗した場合はエラー コード。  
  
## <a name="remarks"></a>コメント  
 アクティブ スクリプトのコンテキストが必要です。  
  
 呼び出しは、別の COM アパートメントまたは同じ MTA の別のスレッドから行われる必要があります。  
  
 この API は、エッジ モードでのみサポートされます。  
  
> [!CAUTION]
>  PInvoke は、現在この API ではサポートされていません。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)