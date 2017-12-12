---
title: JsSerializedScriptUnloadCallback typedef | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d18c392-cca0-411e-9f2b-0d788b16161a
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f485d31367f189231d354c653c8e58cc8656eb9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="jsserializedscriptunloadcallback-typedef"></a>JsSerializedScriptUnloadCallback typedef
スクリプトの実行に関連するリソースがすべて終了したときに、ランタイムによって呼び出されます。     この時点で、呼び出し元はソース (読み込まれている場合)、バイト コード、およびコンテキストを解放する必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
 typedef void (CALLBACK * JsSerializedScriptUnloadCallback)(  
  _In_ JsSourceContext sourceContext  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `sourceContext`  
 `JsParseSerializedScriptWithCallback` または `JsRunSerializedScriptWithCallback`に渡されるコンテキスト。  
  
## <a name="remarks"></a>コメント  
  
> [!WARNING]
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)