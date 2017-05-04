---
title: "IActiveScriptStats::GetStat | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptStats.GetStat
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptStats::GetStat"
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStats::GetStat
標準的なスクリプトの統計情報は 1 を返します。  
  
## 構文  
  
```  
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### パラメーター  
 `stid`  
 \[入力\]取得する統計情報を指定します。  値である必要があります:  
  
|定数|値|説明|  
|--------|-------|--------|  
|SCRIPTSTAT\_STATEMENT\_COUNT|1|呼び出されたスクリプトまたは統計情報がリセットされているため、実行されるステートメントの数を返します。|  
  
 `pluHi`  
 \[入力\]統計情報を表す 64 ビット符号なし整数の上位 32 ビット。  
  
 `pluLo`  
 \[入力\]統計情報を表す 64 ビット符号なし整数の下位 32 ビット。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  有効な値は、次の表の値に含まれますが、はありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは標準的なスクリプトの統計情報の 1 返します。  
  
## 参照  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [IActiveScriptStats インターフェイス](../../winscript/reference/iactivescriptstats-interface.md)