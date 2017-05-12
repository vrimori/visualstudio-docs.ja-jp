---
title: "IActiveScriptParse::AddScriptlet | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParse.AddScriptlet
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParse_AddScriptlet"
ms.assetid: 824929f4-4dd3-473a-92d9-0b96acea2f14
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParse::AddScriptlet
スクリプトにスクリプトレット コードを追加します。  このメソッドは、スクリプトの永続的な状態がホストのドキュメントに絡み合うホストがスクリプトを復元する必要がある `IPersist*` のインターフェイスを通じてではなく、環境で使用されます。  プライマリ例では、組み込みイベント \(たとえば、ONCLICK\= "」button1.text\='Exit アタッチされる HTML の文書に埋め込まれている\) にコードのスクリプトレットを可能にする HTML スクリプト言語です。  
  
## 構文  
  
```  
HRESULT AddScriptlet(  
    LPCOLESTR pstrDefaultName,       // address of default name of scriptlet  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    LPCOLESTR pstrSubItemName,       // address of subitem name  
    LPCOLESTR pstrEventName,         // address of event name  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    BSTR *pbstrName,                 // address of actual name of scriptlet  
    EXCEPINFO *pexcepinfo            // address of exception information  
);  
```  
  
#### パラメーター  
 `pstrDefaultName`  
 \[入力\]スクリプトレットに関連付ける既定の名前のアドレス。  スクリプトレットが情報を提示する \(ONCLICK を前の例のように\) 指定スクリプトレットを識別するために、この名前が使用されます。  このパラメーターが `NULL`の場合、スクリプト エンジンに一意の名前が、必要に応じて生成します。  
  
 `pstrCode`  
 \[入力\]追加するスクリプトレットのテキストのアドレス。  この文字列の解釈はスクリプト言語によって異なります。  
  
 `pstrItemName`  
 \[入力\]の項目の名前を含むバッファーのアドレスは、このスクリプトレットに関連付けられています。  このパラメーターは、`pstrSubItemName`に加えて、スクリプトレットがイベント ハンドラーであるオブジェクトを識別します。  
  
 `pstrSubItemName`  
 \[出力\]このスクリプトレットが関連付けられた名前付きの項目の `subobject` の名前を含むバッファーのアドレス; この名前は、名前付きの項目の型情報で調べる必要があります。  このパラメーターはスクリプトレットが `subitem`の代わりに名前付きの項目に関連付けられる null 値です。  このパラメーターは、`pstrItemName`に加えて、スクリプトレットがイベント ハンドラーで特定のオブジェクトを指定します。  
  
 `pstrEventName`  
 \[入力\]スクリプトレットがイベント ハンドラーであるイベント名を含むバッファーのアドレス。  
  
 `pstrDelimiter`  
 \[入力\]終わりのスクリプトレットの区切り記号のアドレス。  `pstrCode` のパラメーターがテキスト ストリームから解析されると、通常ホストは、スクリプトレットの終了を検出する 2 つ単一引用符などの区切り記号を、\(」\) を使用します。  このパラメーターは、使用するホスト区切り記号を指定します。条件付きのプリミティブな前処理を提供するためにスクリプト エンジンができます \(たとえば、単一引用符を「\[入力\]区切り記号として使用する単一引用符を 2 つに置き換えてください。  は、スクリプト エンジンがどのように使用できます。この情報は、スクリプト エンジンによって異なります \(および\)。  スクリプトレットの終了をマークした場合にホストが区切り記号を使用しない場合は無効にするには、このパラメーターをに設定します。  
  
 `dwSourceContextCookie`  
 \[入力\]デバッグに使用されるアプリケーション定義の値。  
  
 `ulStartingLineNumber`  
 \[入力\]どの行で分析を開始位置を指定する始まる値。  
  
 `dwFlags`  
 \[入力\]フラグはスクリプトレットに関連付けられています。  次の値の組み合わせがあります:  
  
|戻り値|説明|  
|---------|--------|  
|SCRIPTTEXT\_ISVISIBLE|スクリプトのテキストがスクリプトの名前空間のグローバル メソッドとして表示され、\(したがって呼び出し可能\) 名前で必要であることを示します。|  
|SCRIPTTEXT\_ISPERSISTENT|スクリプト エンジンが \(たとえば、`IPersist*::Save`の呼び出しにより\) 保存またはスクリプト エンジンが初期化された状態に遷移を通じてリセットされた場合、この呼び出しの間に追加するコードを保存することを示します。  この状態に関する詳細については、スクリプト エンジンの状態を参照してください。|  
  
 `pbstrName` ,  
 \[入力\]スクリプトレットの識別に使用する実際の名前。  これは、優先順であることです: 明示的にスクリプトレットのテキスト、`pstrDefaultName`で提供される既定の名前またはスクリプト エンジンによって合成される一意の名前で指定された名前。  
  
 `pexcepinfo` ,  
 \[入力\]例外情報が格納された構造体のアドレス。  この構造は DISP\_E\_EXCEPTION が返されると指定してください。  
  
## 戻り値  
 次の値の場合: 1  
  
|戻り値|説明|  
|---------|--------|  
|`S_OK`|成功。|  
|`DISP_E_EXCEPTION`|例外はスクリプトレットの分析で発生した。  `pexcepinfo` のパラメーターは例外に関する情報を格納します。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_NOTIMPL`|このメソッドはできません; スクリプト エンジンはイベント沈降のスクリプトレットを追加することはできません。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_UNEXPECTED`|呼び出し \(たとえば、スクリプト エンジンはまだ読み込まれていないか、初期化されず、および\) がありません。したがって失敗されていません。|  
|`OLESCRIPT_E_INVALIDNAME`|指定されている既定の名前は、このスクリプト言語では無効です。|  
|`OLESCRIPT_E_SYNTAX`|未指定の構文スクリプトレットでエラーが発生しました。|  
  
## 参照  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)