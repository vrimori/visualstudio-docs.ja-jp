---
title: "IActiveScriptSite::GetLCID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetLCID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetLCID"
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetLCID
ホストのユーザー インターフェイスに関連付けられているロケール識別子を取得します。  スクリプト エンジンは、エンジンによって生成されたエラー文字列などのユーザー インターフェイス要素が適切な言語に表示されるように、識別子を使用します。  
  
## 構文  
  
```  
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### パラメーター  
 `plcid`  
 \[入力\]ユーザー インターフェイス要素のロケール識別子を受け取る変数のアドレスは、スクリプト エンジンによって表示されます。  
  
## 戻り値  
 次の値の場合: 1  
  
|戻り値|説明|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_NOTIMPL`|このメソッドは実装されていません。  システム定義のロケールを使用します。|  
|`E_POINTER`|無効なポインターが指定されました。|  
  
## 解説  
 このメソッドがを返した場合、`E_NOTIMPL`システム定義のロケール識別子を使用する必要があります。  
  
## 参照  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)