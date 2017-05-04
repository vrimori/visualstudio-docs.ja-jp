---
title: "IDebugStackFrame::GetLanguageString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrame.GetLanguageString
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrame::GetLanguageString"
ms.assetid: 561d6306-f214-422f-abc9-b502cbfbe208
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame::GetLanguageString
言語の短い場合、長いテキストの説明を返します。  
  
## 構文  
  
```  
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### パラメーター  
 `fLong`  
 \[入力\] `TRUE` が長い説明を返し、`FALSE` が短い説明を返す場合、フラグを設定します。  
  
 `pbstrLanguage`  
 \[出力\]言語の説明。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 通常 `fLong` が `FALSE`場合、このメソッドは、スタック フレームに関連付けられている言語の名前のみです。  `fLong` が `TRUE`の場合、このメソッドは製品の詳細な説明を提供する可能性があります。  
  
## 参照  
 [IDebugStackFrame インターフェイス](../../winscript/reference/idebugstackframe-interface.md)