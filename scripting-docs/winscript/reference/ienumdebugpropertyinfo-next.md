---
title: IEnumDebugPropertyInfo::Next |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Next
ms.assetid: 052837ac-1599-49cc-9a5a-ba90f992eeff
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9f3fe796a518fd7d40c5b30f5b45f8a7d946686
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873748"
---
# <a name="ienumdebugpropertyinfonext"></a>IEnumDebugPropertyInfo::Next
指定した数を取得`DebugPropertyInfo`列挙体シーケンス内の構造体。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Next (  
   ULONGcelt,  
   DebugPropertyInfo*rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 [in]数`DebugPropertyInfo`構造体を取得します。  
  
 `rgelt`  
 [out]配列の`DebugPropertyInfo`構造体を取得します。  
  
 `pceltFetched`  
 [out]数を返します`DebugPropertyInfo`構造が実際に取得します。  
  
## <a name="return-value"></a>戻り値  
 有効な返します`HRESULT`、通常`S_OK`します。  
  
## <a name="see-also"></a>関連項目  
 [IEnumDebugPropertyInfo インターフェイス](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo 構造体](../../winscript/reference/debugpropertyinfo-structure.md)