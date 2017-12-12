---
title: JsNativeFunction Typedef | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 56ef6cdf-4ca9-4f7c-b953-e661addb1a8e
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33cf475dd6a17434ea132647b7d8bde833f0de9e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="jsnativefunction-typedef"></a>JsNativeFunction Typedef
関数コールバック。  
  
## <a name="syntax"></a>構文  
  
```  
typedef _Ret_maybenull_ JsValueRef (CALLBACK * JsNativeFunction)(  
   _In_ JsValueRef callee,  
   _In_ bool isConstructCall,  
   _In_ JsValueRef *arguments,  
   _In_ unsigned short argumentCount  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 呼び出し先  
 呼び出されている関数を表す `Function` オブジェクト。  
  
 isConstructCall  
 これが通常の呼び出しまたは "新しい" 呼び出しのいずれであるかを示します。  
  
 引数  
 呼び出しの引数。  
  
 argumentCount  
 引数の数。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 呼び出しの結果 (存在する場合)。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)