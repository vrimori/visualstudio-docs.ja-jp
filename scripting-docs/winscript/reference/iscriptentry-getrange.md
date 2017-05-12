---
title: "IScriptEntry::GetRange | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetRange
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetRange"
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetRange
エントリの開始位置と長さを返します。  
  
## 構文  
  
```  
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### パラメーター  
 `pichMin`  
 \[入力\]スクリプトのブロックを指定する `IScriptEntry` オブジェクトの場合、は 0 を返します。  
  
 関数オブジェクトを指定する `IScriptEntry` のオブジェクトの場合、は、現在のスクリプト ブロックの関数の開始位置。  
  
 `IScriptScriptlet` のオブジェクトに対して、は 0 を返します。  
  
 `pcch`  
 \[入力\]スクリプトのブロックを指定する `IScriptEntry` のオブジェクト、テキストの長さを返します。  
  
 関数オブジェクトを指定する `IScriptEntry` のオブジェクトに対して、は関数定義の長さ。  
  
 `IScriptScriptlet` のオブジェクトに対して、は、エントリの長さ。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
  
## 参照  
 [IScriptEntry インターフェイス](../../winscript/reference/iscriptentry-interface.md)