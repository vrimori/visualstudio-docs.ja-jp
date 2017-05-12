---
title: "IActiveScriptStats::GetStatEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptStats.GetStatEx
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptStats::GetStatEx"
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStats::GetStatEx
カスタム スクリプトの統計情報を返します。  
  
## 構文  
  
```  
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### パラメーター  
 `guid`  
 \[入力\]取得する統計情報を指定します。  統計情報が特定の GUID に対応する定義されているセマンティクスは完全にエンジンです。  
  
 `pluHi`  
 \[入力\]統計情報を表す 64 ビット符号なし整数の上位 32 ビット。  
  
 `pluLo`  
 \[入力\]統計情報を表す 64 ビット符号なし整数の下位 32 ビット。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`E_NOTIMPL`|このメソッドは実装されていません。|  
  
## 解説  
 このメソッドは、カスタム スクリプト エンジンが意味のあるカスタム ホストに統計情報を返すことができます。  
  
> [!NOTE]
>  メソッドは現在実装されていません。  
  
## 参照  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [IActiveScriptStats インターフェイス](../../winscript/reference/iactivescriptstats-interface.md)