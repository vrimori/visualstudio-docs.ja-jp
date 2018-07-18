---
title: JsDefineProperty 関数 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsDefineProperty
helpviewer_keywords:
- JsDefineProperty function
ms.assetid: b2cf48d6-eb40-457c-aa8b-b16a50dc5d6a
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f929dd875b2ba8bf95db8d5970a770ce2859484
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24567852"
---
# <a name="jsdefineproperty-function"></a>JsDefineProperty 関数
プロパティ記述子から新しいオブジェクトの独自のプロパティを定義します。  
  
## <a name="syntax"></a>構文  
  
```  
STDAPI_(JsErrorCode) JsDefineProperty(  
   _In_ JsValueRef object,  
   _In_ JsPropertyIdRef propertyId,  
   _In_ JsValueRef propertyDescriptor,  
   _Out_ bool *result  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `object`  
 プロパティを含むオブジェクト。  
  
 `propertyId`  
 プロパティの ID。  
  
 `propertyDescriptor`  
 プロパティ記述子。  
  
 `result`  
 プロパティが定義されたかどうか。  
  
## <a name="return-value"></a>戻り値  
 操作が成功した場合はコード `JsNoError` 、操作が失敗した場合はエラー コード。  
  
## <a name="remarks"></a>コメント  
 アクティブ スクリプトのコンテキストが必要です。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)