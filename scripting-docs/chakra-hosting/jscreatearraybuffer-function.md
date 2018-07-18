---
title: JsCreateArrayBuffer 関数 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c9e74184-7dd9-41a7-a1fe-9575e1701392
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9fa67e924b56bea2b4cb1f6d9257ed234e1ea77
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24567672"
---
# <a name="jscreatearraybuffer-function"></a>JsCreateArrayBuffer 関数
Javascript `ArrayBuffer` オブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
STDAPI_(JsErrorCode) JsCreateArrayBuffer(  
   _In_ unsigned int byteLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `byteLength`  
 ArrayBuffer 内のバイト数。  
  
 `result`  
 新しい ArrayBuffer オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 操作が成功した場合はコード `JsNoError` 、操作が失敗した場合はエラー コード。  
  
## <a name="remarks"></a>コメント  
 アクティブ スクリプトのコンテキストが必要です。  
  
 この API は、エッジ モードでのみサポートされます。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)