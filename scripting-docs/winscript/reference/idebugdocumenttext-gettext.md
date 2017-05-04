---
title: "IDebugDocumentText::GetText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetText
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetText"
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetText
文字位置の範囲に関連付けられた文字や文字の属性を取得します。  
  
## 構文  
  
```  
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### パラメーター  
 `cCharacterPosition`  
 \[入力\]文字位置の範囲の開始位置。  
  
 `pcharText`  
 \[入力、出力\] A 文字のテキスト バッファー。  バッファーは `cMaxChars` の文字を格納するのに十分な大きさが必要です。  このパラメーターが NULL の場合、メソッドは文字を返しません。  
  
 `pstaTextAttr`  
 \[入力、出力\] A 文字の属性のバッファー。  バッファーは `cMaxChars` の文字を格納するのに十分な大きさが必要です。  このパラメーターが NULL の場合、メソッドは属性を返しません。  
  
 `pcNumChars`  
 \[入力、出力\]文字と属性の数。  このパラメーターは、このメソッドを呼び出す前にゼロに設定する必要があります。  
  
 `cMaxChars`  
 \[入力\]文字位置の範囲の文字数。  文字の最大数を返すように指定します。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、文字を取得しますか、または文字位置に関連付けられた文字の属性の範囲。  文字位置のスコープは、文字位置といくつかの文字によって指定されます。  
  
## 参照  
 [IDebugDocumentText インターフェイス](../../winscript/reference/idebugdocumenttext-interface.md)   
 [SOURCE\_TEXT\_ATTR 列挙型](../../winscript/reference/source-text-attr-enumeration.md)