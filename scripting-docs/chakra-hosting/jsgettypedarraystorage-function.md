---
title: JsGetTypedArrayStorage 関数 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 52e4ac5f-cc71-456d-95de-a48f7327503d
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b6f4dc99c219c2ebba631c42493bc194148b497
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568702"
---
# <a name="jsgettypedarraystorage-function"></a>JsGetTypedArrayStorage 関数
型指定された配列によって使用される、基になるメモリ ストレージを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
STDAPI_(JsErrorCode) JsGetTypedArrayStorage(  
   _In_ JsValueRef typedArray,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength,  
   _Out_opt_ JsTypedArrayType *arrayType,  
   _Out_opt_ int *elementSize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `typedArray`  
 型指定された配列のインスタンス。  
  
 `buffer`  
 配列のバッファー。 返されたバッファーの有効期間は、配列の有効期間と同じです。 バッファー ポインターは、ガベージ コレクションのための配列への参照としてはカウントされません。  
  
 `bufferLength`  
 バッファー内のバイト数。  
  
 `arrayType`  
 配列の型。  
  
 `elementSize`  
 配列の要素のサイズ。  
  
## <a name="return-value"></a>戻り値  
 操作が成功した場合はコード `JsNoError` 、操作が失敗した場合はエラー コード。  
  
## <a name="remarks"></a>コメント  
 アクティブ スクリプトのコンテキストが必要です。  
  
 この API は、エッジ モードでのみサポートされます。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)