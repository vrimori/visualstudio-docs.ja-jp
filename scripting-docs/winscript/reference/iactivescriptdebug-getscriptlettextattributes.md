---
title: "IActiveScriptDebug::GetScriptletTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptDebug.GetScriptletTextAttributes
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptDebug::GetScriptletTextAttributes"
ms.assetid: b3990d86-5fdf-4c9f-9678-3f4b808c7ca8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug::GetScriptletTextAttributes
任意スクリプトレットのテキスト属性を返します。  
  
## 構文  
  
```  
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### パラメーター  
 `pstrCode`  
 \[入力\]スクリプトレットのテキスト。  この終了する文字列が null である必要はありません。  
  
 `uNumCodeChars`  
 \[入力\]スクリプトレットのテキスト文字の数。  
  
 `pstrDelimiter`  
 \[入力\]終わりのスクリプトレットの区切り記号のアドレス。  `pstrCode` がテキスト ストリームから解析されると、通常ホストは、スクリプトレットの終了を検出する 2 つ単一引用符などの区切り記号を、\(」\) を使用します。  このパラメーターは、使用するホスト区切り記号を指定します。条件付きのプリミティブな前処理を提供するためにスクリプト エンジンができます \(たとえば、単一引用符を「\[入力\]区切り記号として使用する単一引用符を 2 つに置き換えてください。  は、スクリプト エンジンが連携をこの情報は、スクリプト エンジンによって異なります \(および\)。  スクリプトレットの終了をマークした場合にホストが区切り記号を使用しない場合は無効にするには、このパラメーターをに設定します。  
  
 `dwFlags`  
 \[入力\]フラグはスクリプトレットに関連付けられています。  これらの値の組み合わせがあります:  
  
|定数|値|説明|  
|--------|-------|--------|  
|GETATTRTYPE\_DEPSCAN|0x0001|識別子とドット演算子を SOURCETEXT\_ATTR\_IDENTIFIER で識別される必要があり、SOURCETEXT\_ATTR\_MEMBERLOOKUP がフラグを設定するには、に示します。|  
|GETATTRFLAG\_THIS|0x0100|現在のオブジェクトの識別子が SOURCETEXT\_ATTR\_THIS フラグによって識別されることを示します。|  
|GETATTRFLAG\_HUMANTEXT|0x8000|SOURCETEXT\_ATTR\_HUMANTEXT フラグを使用して文字列の内容とコメント テキストが識別されることを示します。|  
  
 `pattr`  
 \[入力、出力\]返される属性を含むバッファー。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 `IDebugDocumentText` のインターフェイスを実装するスマート `IDebugDocumentText::GetText` ホストは、メソッドの呼び出しに代行させるには、このメソッドを使用できます。  
  
 この呼び出しはスクリプトレットが式で傾向で、スクリプト ブロックの別の構文を持つ場合があるため、提供されます。  ものと同じ構文がある場合は、このメソッドの実装では `GetScriptTextAttributes` のメソッドの実装と同じものです。  
  
## 参照  
 [IActiveScriptDebug インターフェイス](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)   
 [IDebugDocumentText インターフェイス](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE\_TEXT\_ATTR 列挙型](../../winscript/reference/source-text-attr-enumeration.md)