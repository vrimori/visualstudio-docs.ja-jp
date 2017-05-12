---
title: "IDispatchEx::GetDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetDispID メソッド"
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetDispID
`IDispatchEx::InvokeEx`以降のの呼び出しで使用できる任意に対応する単一のメンバー名をマップします。  
  
## 構文  
  
```  
 HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### パラメーター  
 `bstrName`  
 割り当てられる名前で渡された。  
  
 `grfdex`  
 メンバーの識別子を取得するためのオプションが決まります。  これは、次の値の組み合わせです:  
  
|値|説明|  
|-------|--------|  
|fdexNameCaseSensitive|その要求は大文字と小文字を区別して検索名前で実行されます。  大文字と小文字を区別して検索をサポートしていないオブジェクトでは無視されますがあります。|  
|fdexNameEnsure|既にあるメンバーを作成する必要があります。  新しいメンバーが `VT_EMPTY`値で作成する必要があります。|  
|fdexNameImplicit|ベース オブジェクトが明示的に指定されていない場合に、呼び出し元が特定の名前のメンバーをオブジェクトを検索していることを示します。|  
|fdexNameCaseInsensitive|その要求は大文字と小文字を区別しない方法で名前検索されます。  大文字小検索をサポートしていないオブジェクトでは無視されますがあります。|  
  
 `pid`  
 任意の呼び出し元が結果を受け取るため、割り当てられた位置へのポインター。  エラーが発生すると、`pid` は DISPID\_UNKNOWN が含まれます。  
  
## 戻り値  
 次の値の場合: 1  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`E_OUTOFMEMORY`|メモリが不足しています。|  
|`DISP_E_UNKNOWNNAME`|名前は不明ですいません。|  
  
## 解説  
 `GetIDsOfNames` の代わりに`GetDispID` が特定のメンバーの DISPID を取得するために使用できます。  
  
 `IDispatchEx` がメンバーの追加および削除できるため、任意のセットは、オブジェクトの有効期間にわたって一定に残りません。  
  
 `IDispatch::GetIDsOfNames` の `riid` の未使用のパラメーターが削除されました。  
  
## 使用例  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## 参照  
 [IDispatchEx インターフェイス](../../winscript/reference/idispatchex-interface.md)