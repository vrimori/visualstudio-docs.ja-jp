---
title: "IScriptEntry::SetItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetItemName"
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptEntry::SetItemName
`IScriptEntry` のオブジェクトを識別する項目の名前を設定します。  
  
## 構文  
  
```  
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### パラメーター  
 `psz`  
 \[入力\]の項目の名前を含むバッファーのアドレス。  ホストによって項目の名前にエントリを識別するために使用されます。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`E_FAIL`|メソッドは成功しませんでした。|  
  
## 解説  
 `IScriptEntry` のオブジェクト、このメソッドは `S_OK`を返します。  
  
 `IScriptEntry` \(から派生\) に `IScriptScriptlet` のオブジェクト `E_FAIL`、このメソッドはを返します。  `IScriptScriptlet` のオブジェクト、項目の名前は [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) によって設定され、変更できません。  
  
## 参照  
 [IScriptEntry インターフェイス](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)