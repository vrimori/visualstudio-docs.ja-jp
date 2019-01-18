---
title: IEnumDebugPropertyInfo::Clone |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Clone
ms.assetid: ba6bdfdb-4c12-475c-bafc-efa6c109d7ee
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cfdd584f607638a5a8e91ff069e0f5a87329533e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344734"
---
# <a name="ienumdebugpropertyinfoclone"></a>IEnumDebugPropertyInfo::Clone
現在の列挙子と同じ列挙状態を格納する列挙子を作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT Clone (  
   IEnumDebugPropertyInfo** ppEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppEnum`  
 [out]複製された返します`IEnumDebugPropertyInfo`インターフェイス。  
  
## <a name="return-value"></a>戻り値  
 有効な返します`HRESULT`、通常`S_OK`します。  
  
## <a name="see-also"></a>関連項目  
 [IEnumDebugPropertyInfo インターフェイス](../../winscript/reference/ienumdebugpropertyinfo-interface.md)