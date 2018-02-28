---
title: "IDispatchEx::GetNameSpaceParent |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDispatchEx.GetNameSpaceParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNameSpaceParent method
ms.assetid: 0b077d39-2fd6-4390-8cd5-128d9b8dc90c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12168ddb5f65c62e81a8f724cacf8b3fd4a1b3a9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexgetnamespaceparent"></a>IDispatchEx::GetNameSpaceParent
オブジェクトの名前空間の親のインターフェイスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetNameSpaceParent(  
   IUnknown **ppunk  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppunk`  
 アドレス、`IUnknown`名前空間の親のインターフェイスを受信するためのインターフェイス ポインター。  
  
## <a name="return-value"></a>戻り値  
 返します`S_OK`正常終了した場合、またはそれ以外の場合、OLE 定義のエラー コード。  
  
## <a name="see-also"></a>関連項目  
 [IDispatchEx インターフェイス](../../winscript/reference/idispatchex-interface.md)