---
title: "JsCreateContext 関数 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsCreateContext
helpviewer_keywords: JsCreateContext function
ms.assetid: aceca043-2c73-4029-a06c-8ad6695109cf
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee756158401468ee00007a764e18a0846f35a3dc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="jscreatecontext-function"></a>JsCreateContext 関数
実行中のスクリプトのスクリプト コンテキストを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ JsContextRef *newContext);  
  
// Legacy mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _In_ IDebugApplication *debugApplication,  
   _Out_ JsContextRef *newContext  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `runtime`  
 スクリプト コンテキストを作成するランタイム。  
  
 `debugApplication`  
 デバッグに使用するデバッグ アプリケーション。 このパラメーターは null でもかまいません。その場合、コンテキストでデバッグは無効です。  
  
 `newContext`  
 作成されるスクリプトのコンテキスト。  
  
## <a name="return-value"></a>戻り値  
 操作が成功した場合はコード `JsNoError` 、操作が失敗した場合はエラー コード。  
  
## <a name="remarks"></a>コメント  
 各スクリプト コンテキストには、他のすべてのスクリプト コンテキストから分離する独自のグローバル オブジェクトがあります。  
  
 エッジ モードでは、`debugApplication` パラメーターがサポートされていません。 エッジ モードでのこの API の使い方の詳細については、[Edge エンジンとレガシ エンジンの対象化](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md)に関するページを参照してください。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)