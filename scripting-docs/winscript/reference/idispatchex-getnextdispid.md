---
title: "IDispatchEx::GetNextDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetNextDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetNextDispID メソッド"
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetNextDispID
オブジェクトのメンバーを列挙します。  
  
## 構文  
  
```  
HRESULT GetNextDispID(  
   DWORD grfdex,  
   DISPID id,  
   DISPID *pid  
);  
```  
  
#### パラメーター  
 `grfdex`  
 項目のセットを列挙するかを決定します。  これは、次の値の組み合わせです:  
  
|値|説明|  
|-------|--------|  
|fdexEnumDefault|オブジェクトが既定の要素を列挙することです。  オブジェクトを要素のセットを列挙します。|  
|fdexEnumAll|オブジェクト要素がすべてを列挙することです。  オブジェクトを要素のセットを列挙します。|  
  
 `id`  
 現在のメンバーを識別します。  GetNextDispID では、この 1 の後で列挙型の項目を取得します。  この識別子を取得または GetDispID 使用 GetNextDispID への前の呼び出し。  DISPID\_STARTENUM の値を最初の項目の最初の識別子を取得するために使用します。  
  
 `pid`  
 列挙体の次の項目の識別子を受け取る変数のアドレスの DISPID。  
  
 メンバーが `DeleteMemberByName` か `DeleteMemberByDispID`によって削除されると、`GetNextDispID`に対して有効なまま `DISPID` があります。  
  
## 戻り値  
 次の値の場合: 1  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`S_FALSE`|列挙型が実行されます。|  
  
## 使用例  
  
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
  
## 参照  
 [IDispatchEx インターフェイス](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](#lrfidispatchexgetnextdispid)   
 [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)   
 [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)