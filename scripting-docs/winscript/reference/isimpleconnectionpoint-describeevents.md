---
title: "ISimpleConnectionPoint::DescribeEvents |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ISimpleConnectionPoint.DescribeEvents
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::DescribeEvents
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 42dab9558d46eae0fbb640c60264a79877708321
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
イベントの指定された範囲内の各イベントの名前と DISPID を返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `iEvent`  
 [in]取得する最初のイベントのインデックス。  
  
 `cEvents`  
 [in]イベント数を取得します。  
  
 `prgid`  
 [out]イベント DISPID 値の配列。  
  
 `prgbstr`  
 [out]イベント名の配列。  
  
 `pcEventsFetched`  
 [out]実際のフェッチ イベントの数。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`S_FALSE`|多くのイベントは、使用可能なよりも要求されました。 使用できないイベントは、DISPID_NULL と null BSTR 表されます。|  
|`E_INVALIDARG`|要素をフェッチしませんでした。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、イベントの指定された範囲内の各イベントの名前と DISPID を返します。  
  
## <a name="see-also"></a>関連項目  
 [ISimpleConnectionPoint インターフェイス](../../winscript/reference/isimpleconnectionpoint-interface.md)