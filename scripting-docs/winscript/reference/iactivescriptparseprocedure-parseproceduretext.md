---
title: "IActiveScriptParseProcedure::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParseProcedure_ParseProcedureText"
ms.assetid: 345a74ae-b4e8-42b2-abd8-633a370e8e7f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParseProcedure::ParseProcedureText
特定のプロシージャ コードを分析し、名前空間にプロシージャを追加します。  
  
## 構文  
  
```  
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### パラメーター  
 `pstrCode`  
 \[入力\]評価するプロシージャのテキストのアドレス。  この文字列の解釈はスクリプト言語によって異なります。  
  
 `pstrFormalParams`  
 \[入力\]プロシージャの仮パラメーター名のアドレス。  パラメーター名は、スクリプト エンジンの適切な区切り記号で区切る必要があります。  名前をかっこで囲む必要ではありません。  
  
 `pstrProcedureName`  
 \[入力\]解析されるプロシージャ名のアドレス。  
  
 `pstrItemName`  
 \[入力\]プロシージャが評価されるコンテキストを提供する項目の名前のアドレス。  このパラメーターがの場合、`NULL`コードは、スクリプト エンジンのグローバル コンテキストで評価されます。  
  
 `punkContext`  
 \[入力\]コンテキストのオブジェクトのアドレス。  このオブジェクトは、アクティブなランタイムのコンテキストを表すためにこのようなコンテキストがデバッガーによって提供される可能性があるデバッグ環境用に予約されています。  このパラメーターが `NULL`場合、エンジンはコンテキストを識別するために `pstrItemName` を使用します。  
  
 `pstrDelimiter`  
 \[入力\]終わりの手順の区切り記号のアドレス。  `pstrCode` がテキスト ストリームから解析されると、通常ホストは、プロシージャの終了を検出する 2 つ単一引用符などの区切り記号を、\(」\) を使用します。  このパラメーターは、使用するホスト区切り記号を指定します。条件付きのプリミティブな前処理を提供するためにスクリプト エンジンができます \(たとえば、単一引用符を「\[入力\]区切り記号として使用する単一引用符を 2 つに置き換えてください。  は、スクリプト エンジンがどのように使用できます。この情報は、スクリプト エンジンによって異なります \(および\)。  手順の最後を示したためにホストが区切り記号を使用しない場合は `NULL` にこのパラメーターを設定します。  
  
 `dwSourceContextCookie`  
 \[入力\]デバッグに使用されるアプリケーション定義の値。  
  
 `ulStartingLineNumber`  
 \[入力\]どの行で分析を開始位置を指定する始まる値。  
  
 `dwFlags`  
 \[入力\]フラグは、プロシージャに関連付けられています。  これらの値の組み合わせがあります:  
  
|値|説明|  
|-------|--------|  
|SCRIPTPROC\_ISEXPRESSION|`pstrCode` のコードはプロシージャの戻り値を表す式であることを示します。  既定では、コードはプロシージャで許可されるステートメントの式、リスト、またはそれ以外でしょうか。スクリプト言語によって含めることができます。|  
|SCRIPTPROC\_IMPLICIT\_THIS|`this` のポインターがプロシージャのスコープに含まれていることを示します。|  
|SCRIPTPROC\_IMPLICIT\_PARENTS|`this` のポインターの親がプロシージャのスコープ内に含まれていることを示します。|  
  
 `ppdisp`  
 \[入力\]グローバル スクリプトのメソッドとプロパティを含むオブジェクトのポインターのアドレス。  スクリプト エンジンがこのようなオブジェクトをサポートしていない場合、`NULL` が返されます。  
  
## 戻り値  
 次の値の場合: 1  
  
|戻り値|説明|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_NOTIMPL`|このメソッドはサポートされていません。  スクリプト エンジンは、名前空間、プロシージャのランタイムの追加をサポートしません。|  
|`E_UNEXPECTED`|呼び出しが想定されていません \(たとえば、スクリプト エンジンが初期化されていない状態または終了状態にあります\)。|  
|`OLESCRIPT_E_SYNTAX`|未指定の手順で構文エラーが発生しました。|  
|`S_FALSE`|スクリプト エンジンはディスパッチ オブジェクトをサポートしていません; `ppdisp` のパラメーターは `NULL`に設定されます。|  
  
## 解説  
 スクリプト コードはこの呼び出し時に評価されることはありません; なく、プロシージャはスクリプトで後で呼び出すことができるスクリプトの状態にコンパイルされます。  
  
## 参照  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)