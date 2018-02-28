---
title: "IEnumDebugExtendedPropertyInfo::Next |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Next
ms.assetid: ac41c9a3-19d1-4596-8a87-01c10b131be3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 343620e4539e9d095f2708ab46077ee0dafd1932
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugextendedpropertyinfonext"></a>IEnumDebugExtendedPropertyInfo::Next
指定した数を取得`ExtendedDebugPropertyInfo`列挙のシーケンス内の構造体。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Next (  
   ULONGcelt,  
   ExtendedDebugPropertyInfo *rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 [in]数`ExtendedDebugPropertyInfo`構造体を取得します。  
  
 `rgelt`  
 [out]配列`ExtendedDebugPropertyInfo`構造体を取得します。  
  
 `pceltFetched`  
 [out]数`ExtendedDebugPropertyInfo`構造が実際に取得します。  
  
## <a name="return-value"></a>戻り値  
 有効な返します`HRESULT`通常`S_OK`です。  
  
## <a name="see-also"></a>関連項目  
 [IEnumDebugExtendedPropertyInfo インターフェイス](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo 構造体](../../winscript/reference/extendeddebugpropertyinfo-structure.md)