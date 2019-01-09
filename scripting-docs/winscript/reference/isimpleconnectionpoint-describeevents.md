---
title: ISimpleConnectionPoint::DescribeEvents |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.DescribeEvents
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::DescribeEvents
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43a20a2d9580c80bc6aea5d22c6a0713f4843634
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088505"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
イベントの指定した範囲内で、DISPID と各イベントの名前を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
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
 [in]取得するイベントの数。  
  
 `prgid`  
 [out]イベントの DISPID 値の配列。  
  
 `prgbstr`  
 [out]イベント名の配列。  
  
 `pcEventsFetched`  
 [out]実際にフェッチされるイベントの数。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`S_FALSE`|使用可能なより多くのイベントは要求されました。 使用できないイベントは、DISPID_NULL と null BSTR で表されます。|  
|`E_INVALIDARG`|要素はフェッチされませんでした。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、イベントの指定した範囲内で、DISPID と各イベントの名前を返します。  
  
## <a name="see-also"></a>関連項目  
 [ISimpleConnectionPoint インターフェイス](../../winscript/reference/isimpleconnectionpoint-interface.md)