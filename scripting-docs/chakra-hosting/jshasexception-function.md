---
title: JsHasException 関数 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsHasException
helpviewer_keywords:
- JsHasException function
ms.assetid: ac7da3ce-c746-4154-bbb8-bcb0859a8d5b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 32334f4b8787bebaffb9553fcdd40f85334462cb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568542"
---
# <a name="jshasexception-function"></a>JsHasException 関数
現在のコンテキストのランタイムが例外状態であるかどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
STDAPI_(JsErrorCode) JsHasException(  
   _Out_ bool *hasException  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `hasException`  
 現在のコンテキストのランタイムが例外状態であるかどうか。  
  
## <a name="return-value"></a>戻り値  
 操作が成功した場合はコード `JsNoError` 、操作が失敗した場合はエラー コード。  
  
## <a name="remarks"></a>コメント  
 (スクリプトの実行結果として、または変換の失敗などの理由により) ランタイムに対する呼び出しで例外が発生した場合、ランタイムは "例外状態" になります。 (例外 API を除く) ランタイムによって作成されたコンテキストに対するすべての呼び出しは、例外がクリアされるまで、`JsErrorInExceptionState` で失敗します。  
  
 現在のコンテキストのランタイムが例外状態である場合、コールバックがエンジンに戻ると、エンジンが自動的に例外を再スローします。  
  
 アクティブ スクリプトのコンテキストが必要です。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)