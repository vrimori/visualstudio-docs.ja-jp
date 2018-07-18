---
title: JsCallFunction 関数 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsCallFunction
helpviewer_keywords:
- JsCallFunction function
ms.assetid: 8a1dca72-d720-4a28-a86e-6809465006fe
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb4ed76fbd387c16a78dae12c519e7a22c185243
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24567692"
---
# <a name="jscallfunction-function"></a>JsCallFunction 関数
関数を呼び出します。  
  
## <a name="syntax"></a>構文  
  
```  
STDAPI_(JsErrorCode) JsCallFunction(  
   _In_ JsValueRef function,  
   _In_reads_(argumentCount) JsValueRef *arguments,  
   _In_ unsigned short argumentCount,  
   _Out_opt_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `function`  
 呼び出す関数。  
  
 `arguments`  
 呼び出しの引数。  
  
 `argumentCount`  
 関数に渡される引数の数。  
  
 `result`  
 関数の呼び出しから返された値 (存在する場合)。  
  
## <a name="return-value"></a>戻り値  
 操作が成功した場合はコード `JsNoError` 、操作が失敗した場合はエラー コード。  
  
## <a name="remarks"></a>コメント  
 アクティブ スクリプトのコンテキストが必要です。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)