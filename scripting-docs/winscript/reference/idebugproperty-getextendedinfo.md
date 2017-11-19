---
title: "IDebugProperty::GetExtendedInfo |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugProperty.GetExtendedInfo
apilocation: scrobj.dll
helpviewer_keywords: IDebugProperty::GetExtendedInfo
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc549ecc4cfa3b3cbbb754585c751b16df2fd8a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
プロパティの情報を拡張を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cInfos`  
 [in]オブジェクトの拡張情報の数。  
  
 `rgguidExtendedInfo`  
 [in]配列`GUID`s は、同時に拡張情報の複数のアイテムを取得できるようにするために渡されます。  
  
 `pExtendedInfo`  
 [out]配列を返します`VARIANT`s 拡張プロパティの情報を取得するために使用できます。  
  
## <a name="return-value"></a>戻り値  
 有効な返します`HRESULT`通常`S_OK`です。  
  
## <a name="remarks"></a>コメント  
 このインターフェイスは、このオブジェクトの情報を拡張を取得します。 使用して取得するのには適していません情報を取得するためにのみ存在する API は、 `IDebugProperty::GetPropertyInfo`)。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)