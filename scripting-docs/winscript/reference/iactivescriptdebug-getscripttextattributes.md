---
title: "IActiveScriptDebug::GetScriptTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptDebug.GetScriptTextAttributes
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptDebug::GetScriptTextAttributes"
ms.assetid: 2e8bda34-db0c-4b2e-a17f-82c4e0dbbc8c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug::GetScriptTextAttributes
スクリプトの任意のテキスト ブロックのテキスト属性を返します。  
  
## 構文  
  
```  
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### パラメーター  
 `pstrCode`  
 \[入力\]スクリプト ブロックのテキスト。  この終了する文字列が null である必要はありません。  
  
 `uNumCodeChars`  
 \[入力\]スクリプト ブロック内のテキストの文字数。  
  
 `pstrDelimiter`  
 \[入力\]終わりのスクリプト ブロックの区切り記号のアドレス。  `pstrCode` がテキスト ストリームから解析されると、通常ホストは、スクリプト ブロックの末尾を検出する 2 つ単一引用符などの区切り記号を、\(」\) を使用します。  このパラメーターは、使用するホスト区切り記号を指定します。条件付きのプリミティブな前処理を提供するためにスクリプト エンジンができます \(たとえば、単一引用符を「\[入力\]区切り記号として使用する単一引用符を 2 つに置き換えてください。  は、スクリプト エンジンが連携をこの情報は、スクリプト エンジンによって異なります \(および\)。  スクリプト ブロックの末尾を示したためにホストが区切り記号を使用しない場合は無効にするには、このパラメーターをに設定します。  
  
 `dwFlags`  
 \[入力\]フラグは、スクリプト ブロックに関連付けられた  これらの値の組み合わせがあります:  
  
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
  
 スクリプト ブロックに対してこのメソッド; `GetScriptletTextAttributes` のメソッドはスクリプトレット用です。  
  
## 参照  
 [IActiveScriptDebug インターフェイス](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)   
 [IDebugDocumentText インターフェイス](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE\_TEXT\_ATTR 列挙型](../../winscript/reference/source-text-attr-enumeration.md)