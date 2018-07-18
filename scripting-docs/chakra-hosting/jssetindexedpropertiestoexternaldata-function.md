---
title: JsSetIndexedPropertiesToExternalData 関数 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: cee2d86d-ed42-4acb-86ef-95a67e63d0d6
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7180c5e233cfd5e448bc9f0d3eb1895e5dfd4aa8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568852"
---
# <a name="jssetindexedpropertiestoexternaldata-function"></a>JsSetIndexedPropertiesToExternalData 関数
オブジェクトのインデックス付きプロパティを外部データに設定します。 外部データは、オブジェクトのインデックス付きプロパティのバック ストアとして使用され、型指定された配列と同様にアクセスされます。  
  
## <a name="syntax"></a>構文  
  
```  
STDAPI_(JsErrorCode) JsSetIndexedPropertiesToExternalData(  
   _In_ JsValueRef object,  
   _In_ void* data,  
   _In_ JsTypedArrayType arrayType,  
   _In_ unsigned int elementLength  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `object`  
 対象となるオブジェクト。  
  
 `data`  
 オブジェクトのインデックス付きプロパティのバック ストアとして使用される外部データ。  
  
 `arrayType`  
 外部データ内の配列要素型。  
  
 `elementLength`  
 外部データ内の配列要素の数。  
  
## <a name="return-value"></a>戻り値  
 操作が成功した場合はコード `JsNoError` 、操作が失敗した場合はエラー コード。  
  
## <a name="remarks"></a>コメント  
 アクティブ スクリプトのコンテキストが必要です。  
  
 この API は、エッジ モードでのみサポートされます。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)