---
title: "IScriptEntry::GetItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetItemName"
ms.assetid: 8f2562f1-8231-4a39-ad79-074f9ec3d403
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IScriptEntry::GetItemName
`IScriptEntry` のオブジェクトを識別する項目の名前を返します。  
  
## 構文  
  
```  
HRESULT GetItemName(  
   BSTR               *pbstr  
);  
```  
  
#### パラメーター  
 `pbstr`  
 \[入力\]の項目の名前を含むバッファーのアドレス。  ホストによって項目の名前にエントリを識別するために使用されます。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 `IScriptScriptlet` に [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)を使用して、項目の名前のオブジェクトを指定します。  そのほかのインターフェイスの場合は、プロパティ [IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)を使用して項目の名前。  
  
## 参照  
 [IScriptEntry インターフェイス](../../winscript/reference/iscriptentry-interface.md)