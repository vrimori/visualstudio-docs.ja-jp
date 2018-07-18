---
title: JsCreateURIError 関数 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsCreateURIError
helpviewer_keywords:
- JsCreateURIError function
ms.assetid: 711fd237-12a2-4ff0-b58a-ad74c91e79fb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9750f9a554cd442c26a45fcc97e70273b15df9ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24567932"
---
# <a name="jscreateurierror-function"></a>JsCreateURIError 関数
新しい JavaScript URIError のエラー オブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
STDAPI_(JsErrorCode) JsCreateURIError(  
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