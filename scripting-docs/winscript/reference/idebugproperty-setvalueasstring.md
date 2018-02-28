---
title: "IDebugProperty::SetValueAsString |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugProperty.SetValueAsString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::SetValueAsString
ms.assetid: cad8d7b2-19a5-4a29-9000-cafdecdc238b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 88a7cba4ec83c5428dd4da4a23ce554702177e76
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertysetvalueasstring"></a>IDebugProperty::SetValueAsString
指定した文字列からのプロパティの値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetValueAsString (  
   LPCOLESTR pszValue,  
   UINTnRadix,  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszValue`  
 [in]設定する値。  
  
 `nRadix`  
 [in]任意の数値情報を解釈するときに使用する基数。  
  
## <a name="return-value"></a>戻り値  
 有効な返します`HRESULT`通常`S_OK`です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)