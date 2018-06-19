---
title: IDispatchEx::GetNextDispID |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNextDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNextDispID method
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ece7bde3230da370c8434cef7f780a92604df34c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728522"
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID
オブジェクトのメンバーを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetNextDispID(  
   DWORD grfdex,  
   DISPID id,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `grfdex`  
 列挙するアイテムのセットが決まります。 これにより、次の値の組み合わせが可能します。  
  
|値|説明|  
|-----------|-------------|  
|fdexEnumDefault|要求は、オブジェクトは、既定の要素を列挙します。 オブジェクトは、任意の要素のセットの列挙が許可されます。|  
|fdexEnumAll|要求は、オブジェクトがすべての要素を列挙します。 オブジェクトは、任意の要素のセットの列挙が許可されます。|  
  
 `id`  
 現在のメンバーを識別します。 GetNextDispID は、この後に、列挙内の項目を取得します。 この識別子を取得するのにには、GetDispID または GetNextDispID を前の呼び出しを使用します。 最初の項目の最初の識別子を取得するのにには、DISPID_STARTENUM 値を使用します。  
  
 `pid`  
 列挙体の次の項目の識別子を受信する DISPID 変数のアドレス。  
  
 によって、メンバーが削除された場合`DeleteMemberByName`または`DeleteMemberByDispID`、`DISPID`の有効なままにしておく必要がある`GetNextDispID`です。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`S_FALSE`|列挙が行われます。|  
  
## <a name="example"></a>例  
  
```  
HRESULT hr;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
  
   // Assign to pdex  
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
   while (hr == NOERROR)  
   {  
      hr = pdex->GetMemberName(dispid, &bstrName);  
      if (!wcscmp(bstrName, OLESTR("Bar")))  
      {  
         SysFreeString(bstrName);  
         return TRUE;  
      }  
      SysFreeString(bstrName);  
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);  
   }  
```  
  
## <a name="see-also"></a>関連項目  
 [IDispatchEx インターフェイス](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](#lrfidispatchexgetnextdispid)   
 [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)   
 [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)