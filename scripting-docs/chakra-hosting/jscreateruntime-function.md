---
title: JsCreateRuntime 関数 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsCreateRuntime
helpviewer_keywords:
- JsCreateRuntime function
ms.assetid: 92d09b89-6593-4d73-a562-88f9fec10228
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93a3df1e7ea76cf76fad9ffde9ccea19f2ba28af
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568142"
---
# <a name="jscreateruntime-function"></a>JsCreateRuntime 関数
新しいランタイムを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsCreateRuntime(  
   _In_ JsRuntimeAttributes attributes,  
   _In_opt_ JsThreadServiceCallback threadService,  
   _Out_ JsRuntimeHandle *runtime);  
  
// Legacy mode signature  
STDAPI_(JsErrorCode) JsCreateRuntime(  
   _In_ JsRuntimeAttributes attributes,  
   _In_ JsRuntimeVersion version,  
   _In_opt_ JsThreadServiceCallback threadService,  
   _Out_ JsRuntimeHandle *runtime  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `attributes`  
 作成するランタイムの属性。  
  
 `version`  
 作成するランタイムのバージョン。  
  
 `threadService`  
 ランタイムのスレッド サービス。 null を使用できます。  
  
 `runtime`  
 作成するランタイム。  
  
## <a name="return-value"></a>戻り値  
 操作が成功した場合はコード `JsNoError` 、操作が失敗した場合はエラー コード。  
  
## <a name="remarks"></a>コメント  
 エッジ モードでは、`version` パラメーターがサポートされていません。 エッジ モードでのこの API の使い方の詳細については、[Edge エンジンとレガシ エンジンの対象化](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md)に関するページを参照してください。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)