---
title: "IActiveScriptAuthor::GetScriptletTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetScriptletTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetScriptletTextAttributes"
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptAuthor::GetScriptletTextAttributes
スクリプトレットのテキスト属性を返します。  
  
## 構文  
  
```  
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR pszCode,  
   ULONG cch,  
   LPCOLESTR pszDelimiter,  
   DWORD dwFlags,  
   SOURCE_TEXT_ATTR *pattr  
);  
```  
  
#### パラメーター  
 `pszCode`  
 \[入力、size\_is \(`cch`\) \] スクリプトレットのテキスト。  この終了する文字列が null である必要はありません。  
  
 `cch`  
 \[入力\] `pszCode` と `pattr` パラメーターとして使用できるサイズ。  
  
 `pszDelimiter`  
 \[入力\]終わりのスクリプトレットの区切り記号のアドレス。  `pszCode` がテキスト ストリームから解析されると、通常ホストは、スクリプトレットの終了を検出するために、区切り記号 \(2 三つの単一引用符など\) を使用します。  スクリプトレットの終了を識別するために区切り記号が使用されていない場合は無効にするには、このパラメーターをに設定します。  
  
 `dwFlags`  
 \[入力\]スクリプトレットのテキスト属性に関連付けられているフラグ。  次の値の組み合わせを指定できます。  
  
|定数|値|説明|  
|--------|-------|--------|  
|GETATTRTYPE\_DEPSCAN|0x0001|SOURCETEXT\_ATTR\_IDENTIFIER の属性を持つ識別し、SOURCETEXT\_ATTR\_MEMBERLOOKUP の属性を持つドット演算子を識別子を指定します。|  
|GETATTRFLAG\_THIS|0x0100|SOURCETEXT\_ATTR\_THIS の属性を持つ現在のオブジェクトを識別します。|  
|GETATTRFLAG\_HUMANTEXT|0x8000|文字列の内容をと SOURCETEXT\_ATTR\_HUMANTEXT の属性を持つコメントのテキストを指定します。|  
  
 `pattr`  
 \[入力、size\_is \(`cch`\) \] スクリプトレット コードの色の情報。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
  
## 参照  
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [SOURCE\_TEXT\_ATTR 列挙型](../../winscript/reference/source-text-attr-enumeration.md)