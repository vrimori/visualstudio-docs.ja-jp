---
title: "IScriptEntry::SetText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ISetEntry::SetText"
ms.assetid: 4605481b-7707-43d1-ab78-a9207d0cf6fe
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::SetText
`IScriptEntry` のスクリプト ブロックに対応する、または `IScriptScriptlet` のイベント ハンドラーに含まれるソース・コードをテキストを設定します。  
  
## 構文  
  
```  
HRESULT SetText(  
   LPCOLESTR          psz  
);  
```  
  
#### パラメーター  
 `psz`  
 \[入力\] `IScriptEntry` のスクリプト ブロックのテキスト \( `IScriptScriptlet` のイベント ハンドラーのソース・コード。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
  
## 参照  
 [IScriptEntry インターフェイス](../../winscript/reference/iscriptentry-interface.md)