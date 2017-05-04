---
title: "IScriptEntry::GetBody | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetBody
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetBody"
ms.assetid: 419c8c11-a1f8-4b97-ab00-e8af2b2f9bfc
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetBody
`IScriptEntry` のスクリプト ブロック、ブロック、関数またはスクリプトレットの本体に対応するテキストを返します。  
  
## 構文  
  
```  
HRESULT GetBody(  
   BSTR               *pbstr  
);  
```  
  
#### パラメーター  
 `pbstr`  
 \[入力\]次のいずれかの本体にあるテキスト:  
  
-   `IScriptEntry` のスクリプト ブロック  
  
-   関数のブロックの `IScriptEntry` 関数  
  
-   `IScriptEntry` のスクリプトレットのイベント ハンドラー  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
  
## 参照  
 [IScriptEntry インターフェイス](../../winscript/reference/iscriptentry-interface.md)