---
title: "IDispatchEx::DeleteMemberByDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.DeleteMemberByDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DeleteMemberByDispID メソッド"
ms.assetid: f61231e5-ba93-4ac3-bde8-d363548356b3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::DeleteMemberByDispID
DISPID にメンバーを削除します。  
  
## 構文  
  
```  
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### パラメーター  
 `id`  
 メンバーの識別子。  ディスパッチ ID を取得または `GetNextDispID` 使用 `GetDispID`。  
  
## 戻り値  
 次の値の場合: 1  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`S_FALSE`|メンバーが存在しますが削除できません。|  
  
## 解説  
 メンバーが削除されると、DISPID は `GetNextDispID`に対して有効である必要があります。  
  
 指定された名前のメンバーが削除され、後で同じ名前のメンバーが再作成される場合、DISPID はと同じです。  大文字と小文字のみが異なるメンバーの名前が「かどうか \(同じ参照先オブジェクトは」です\)。  
  
## 使用例  
  
```  
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## 参照  
 [IDispatchEx インターフェイス](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)