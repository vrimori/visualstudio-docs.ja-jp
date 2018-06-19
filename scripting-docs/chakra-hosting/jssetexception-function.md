---
title: JsSetException 関数 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsSetException
helpviewer_keywords:
- JsSetException function
ms.assetid: c528793a-2e1b-4ee1-bd2e-e63fd547dc40
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5d8fce71f14dedea02e1809fb72281f575f60604
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568592"
---
# <a name="jssetexception-function"></a>JsSetException 関数
現在のコンテキストのランタイムを例外状態に設定します。  
  
## <a name="syntax"></a>構文  
  
```  
STDAPI_(JsErrorCode) JsSetException(  
   _In_ JsValueRef exception  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `exception`  
 現在のコンテキストのランタイムに対して設定する JavaScript 例外。  
  
## <a name="return-value"></a>戻り値  
 エンジンが例外状態に設定されている場合は `JsNoError`、それ以外の場合は失敗コード。  
  
## <a name="remarks"></a>コメント  
 現在のコンテキストのランタイムが既に例外状態である場合、この API は `JsErrorInExceptionState` を返します。  
  
 アクティブ スクリプトのコンテキストが必要です。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)