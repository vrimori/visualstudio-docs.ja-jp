---
title: JsStartDebugging 関数 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsStartDebugging
helpviewer_keywords:
- JsStartDebugging function
ms.assetid: c48ba02d-6d47-466f-a970-02f087d525f3
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd9b7e3deb407d1a1e9d16db38e17c85ccc8c797
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569112"
---
# <a name="jsstartdebugging-function"></a>JsStartDebugging 関数
現在のコンテキストでデバッグを開始します。  
  
## <a name="syntax"></a>構文  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsStartDebugging();  
  
// Legacy mode signature  
STDAPI_(JsErrorCode)  JsStartDebugging(  
   _In_ IDebugApplication *debugApplication  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `debugApplication`  
 デバッグに使用するデバッグ アプリケーション。  
  
## <a name="return-value"></a>戻り値  
 操作が成功した場合はコード `JsNoError` 、操作が失敗した場合はエラー コード。  
  
## <a name="remarks"></a>コメント  
 ホストは、この API を呼び出す前に少なくとも一度 `COINIT_MULTITHREADED` または `COINIT_APARTMENTTHREADED` と共に `CoInitializeEx` が呼び出されることを確認する必要があります。  
  
 エッジ モードでは、`debugApplication` パラメーターがサポートされていません。 エッジ モードでのこの API の使い方の詳細については、[Edge エンジンとレガシ エンジンの対象化](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md)に関するページを参照してください。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)