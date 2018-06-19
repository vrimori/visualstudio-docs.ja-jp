---
title: JsValueToVariant 関数 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsValueToVariant
helpviewer_keywords:
- JsValueToVariant function
ms.assetid: 070244be-a69d-4b78-971b-69c0579c03cf
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2beb0a72a8e19d38d80ab8bf29ce0478ba7f481f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568902"
---
# <a name="jsvaluetovariant-function"></a>JsValueToVariant 関数
JavaScript の値の投影として渡された `VARIANT` を初期化します。  
  
## <a name="syntax"></a>構文  
  
```  
STDAPI_(JsErrorCode) JsValueToVariant(  
   _In_ JsValueRef object,  
   _Out_ VARIANT *variant  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `object`  
 `VARIANT` として投影する JavaScript の値。  
  
 `variant`  
 投影として初期化される `VARIANT` 構造体へのポインター。  
  
## <a name="return-value"></a>戻り値  
  
## <a name="remarks"></a>コメント  
 投影された JavaScript にオブジェクトを呼び出すために、COM のオートメーション クライアントによって、投影の `VARIANT` を使用できます。  
  
 アクティブ スクリプトのコンテキストが必要です。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)