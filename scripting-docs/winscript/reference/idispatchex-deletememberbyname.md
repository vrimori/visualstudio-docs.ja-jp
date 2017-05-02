---
title: "IDispatchEx::DeleteMemberByName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.DeleteMemberByName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DeleteMemberByName メソッド"
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::DeleteMemberByName
メンバーを名前で削除します。  
  
## 構文  
  
```  
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### パラメーター  
 `bstrName`  
 削除するメンバーの名前。  
  
 `grfdex`  
 メンバー名の大文字と小文字を区別するかどうかを判定します。  これは次の値の 1 つです:  
  
|値|説明|  
|-------|--------|  
|fdexNameCaseSensitive|その要求は大文字と小文字を区別して検索名前で実行されます。  大文字と小文字を区別して検索をサポートしていないオブジェクトによって無視できます。|  
|fdexNameCaseInsensitive|その要求は大文字と小文字を区別しない方法で名前検索されます。  大文字小検索をサポートしていないオブジェクトによって無視できます。|  
  
## 戻り値  
 次の値の場合: 1  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`S_FALSE`|メンバーが存在しますが削除できません。|  
  
## 解説  
 メンバーが削除されると、DISPID は `GetNextDispID`に対して有効である必要があります。  
  
 指定された名前のメンバーが削除され、後で同じ名前のメンバーが再作成される場合、DISPID はと同じです。  大文字と小文字のみが異なるメンバーが「かどうかは同じです \(」オブジェクト参照先。\)  
  
## 使用例  
  
```  
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## 参照  
 [IDispatchEx インターフェイス](../../winscript/reference/idispatchex-interface.md)