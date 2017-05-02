---
title: "IApplicationDebugger::onDebugOutput | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.onDebugOutput
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::onDebugOutput"
ms.assetid: 978d8bcf-16dc-4f24-a6bc-206adee2b2e9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::onDebugOutput
デバッグ出力のイベントを処理します。  
  
## 構文  
  
```  
HRESULT onDebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### パラメーター  
 `pstr`  
 \[入力\]デバッガーで表示する文字列。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 デバッガーは、通常、出力ウィンドウの `pstr` を表示します。  
  
 このメソッドは `IDebugApplication::DebugOutput` が呼び出されたときに呼び出されます。  
  
## 参照  
 [IApplicationDebugger インターフェイス](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)