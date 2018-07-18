---
title: JsCreateTypeError 関数 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsCreateTypeError
helpviewer_keywords:
- JsCreateTypeError function
ms.assetid: 8ef7bb77-2c98-482a-bccb-1f0fe2b826f5
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 42404084d7f6f75e5cdec6b9e4bf06f29b8a2136
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24567862"
---
# <a name="jscreatetypeerror-function"></a>JsCreateTypeError 関数
新しい JavaScript TypeError のエラー オブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
STDAPI_(JsErrorCode) JsCreateTypeError(  
   _In_ JsValueRef message,  
   _Out_ JsValueRef *error  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `message`  
 エラー オブジェクトのメッセージ。  
  
 `error`  
 新しいエラー オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 操作が成功した場合はコード `JsNoError` 、操作が失敗した場合はエラー コード。  
  
## <a name="remarks"></a>コメント  
 アクティブ スクリプトのコンテキストが必要です。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)