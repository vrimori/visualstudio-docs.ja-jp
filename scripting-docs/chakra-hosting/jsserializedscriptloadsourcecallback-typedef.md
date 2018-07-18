---
title: JsSerializedScriptLoadSourceCallback Typedef | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9406c488-76ac-49e5-b305-39751f3412ea
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ff3bc206cf3779023a13166f30e8f4f719e7ebe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568722"
---
# <a name="jsserializedscriptloadsourcecallback-typedef"></a>JsSerializedScriptLoadSourceCallback Typedef
ランタイムによって、シリアル化されたスクリプトのソース コードを読み込むために呼び出されます。     呼び出し元では、 `JsSerializedScriptUnloadCallback`までスクリプト バッファーを有効な状態に保つ必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
typedef bool (CALLBACK * JsSerializedScriptLoadSourceCallback)(  
  _In_ JsSourceContextsourceContext,  
  _Outptr_result_z_ const wchar_t** scriptBuffer  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `sourceContext`  
 `JsParseSerializedScriptWithCallback` または `JsRunSerializedScriptWithCallback`に渡されるコンテキスト。  
  
 `scriptBuffer`  
 返されるスクリプト。  
  
## <a name="remarks"></a>コメント  
  
> [!WARNING]
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)