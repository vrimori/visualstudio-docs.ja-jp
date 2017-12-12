---
title: "JsSerializeScript 関数 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsSerializeScript
helpviewer_keywords: JsSerializeScript function
ms.assetid: ca42c194-e1c1-407d-b542-b9d494e3ac4e
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 92bc6c1de0f2cd43dfe9566413fb64188fd5a382
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="jsserializescript-function"></a>JsSerializeScript 関数
再使用できる以上の解析済みスクリプトをバッファーにシリアル化します。  
  
## <a name="syntax"></a>構文  
  
```  
STDAPI_(JsErrorCode) JsSerializeScript(  
   _In_z_ const wchar_t *script,  
   _Out_writes_to_opt_(*bufferSize,  
   *bufferSize) BYTE *buffer,  
   _Inout_ unsigned long *bufferSize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `script`  
 シリアル化するスクリプト。  
  
 `buffer`  
 シリアル化されたスクリプトを格納するバッファー。 null を使用できます。  
  
 `bufferSize`  
 開始時にはバッファーのサイズ (バイト)、終了時にはシリアル化されたスクリプトを保持するのに必要なバッファーのサイズ (バイト)。  
  
## <a name="return-value"></a>戻り値  
 操作が成功した場合はコード `JsNoError` 、操作が失敗した場合はエラー コード。  
  
## <a name="remarks"></a>コメント  
 `JsSerializeScript` は、スクリプトを解析した後、ランタイムに依存しない形式でスクリプトの解析済みフォームを格納します。 これによって、シリアル化済みスクリプトは、スクリプトの再解析を行う必要なく、任意のランタイムで逆シリアル化できます。  
  
 アクティブ スクリプトのコンテキストが必要です。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)