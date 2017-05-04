---
title: "IActiveScriptParseProcedureOld::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedureOld.ParseProcedureText
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptParseProcedureOld::ParseProcedureText"
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptParseProcedureOld::ParseProcedureText
特定のプロシージャ コードを分析し、名前空間には匿名のプロシージャを追加します。  
  
## 構文  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### パラメーター  
 `pstrCode`  
 \[入力\]評価するプロシージャのテキスト。  この文字列の解釈はスクリプト言語によって異なります。  
  
 `pstrFormalParams`  
 \[入力\]プロシージャの仮パラメーター名。  パラメーター名は、スクリプト エンジンの適切な区切り記号で区切る必要があります。  名前をかっこで囲む必要ではありません。  
  
 `pstrItemName`  
 \[入力\]プロシージャが評価されるコンテキストを提供する名前付きの項目の名前。  このパラメーターがの場合、`NULL`コードは、スクリプト エンジンのグローバル コンテキストで評価されます。  
  
 `punkContext`  
 \[入力\]コンテキスト オブジェクト。  このオブジェクトは、アクティブなランタイムのコンテキストを表すためにこのようなコンテキストがデバッガーによって提供される可能性があるデバッグ環境用に予約されています。  このパラメーターが `NULL`場合、エンジンはコンテキストを識別するために `pstrItemName` を使用します。  
  
 `pstrDelimiter`  
 \[入力\]終わりの手順の区切り記号。  `pstrCode` がテキスト ストリームから解析されると、通常ホストは、プロシージャの終了を検出する 2 つ単一引用符などの区切り記号を、\(」\) を使用します。  このパラメーターは、区切り記号を指定し、条件付き使用される、ホスト プリミティブ前処理を提供するためにスクリプト エンジンができます \(たとえば、単一引用符を「\[入力\]区切り記号として使用する単一引用符を 2 つに置き換えてください。  は、スクリプト エンジンが連携をこの情報は、スクリプト エンジンによって異なります \(および\)。  手順の最後を示したためにホストが区切り記号を使用しない場合は `NULL` にこのパラメーターを設定します。  
  
 `dwSourceContextCookie`  
 \[入力\]デバッグに使用されるアプリケーション定義の値。  
  
 `ulStartingLineNumber`  
 \[入力\]どの行で分析を開始するかを指定する始まる値。  
  
 `dwFlags`  
 \[入力\]フラグは、プロシージャに関連付けられています。  これらの値の組み合わせを指定できます。  
  
|定数|値|説明|  
|--------|-------|--------|  
|SCRIPTPROC\_ISEXPRESSION|0x00000020|`pstrCode` のコードはプロシージャの戻り値を表す式であることを示します。|  
|SCRIPTPROC\_IMPLICIT\_THIS|0x00000100|`this` のポインターがプロシージャのスコープに含まれていることを示します。|  
|SCRIPTPROC\_IMPLICIT\_PARENTS|0x00000200|`this` のポインターの親がプロシージャのスコープ内に含まれていることを示します。|  
  
 `ppdisp`  
 \[入力\]既定のメソッドがこのメソッドによって解析されるプロシージャであるディスパッチ ラッパーを返します。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_NOTIMPL`|このメソッドはサポートされていません。  スクリプト エンジンは、名前空間、プロシージャのランタイムの追加をサポートしません。|  
|`E_UNEXPECTED`|呼び出しが想定されていません \(たとえば、スクリプト エンジンが初期化されていない状態または終了状態にあります\)。|  
|`OLESCRIPT_E_SYNTAX`|未指定の手順で構文エラーが発生しました。|  
|`S_FALSE`|スクリプト エンジンはディスパッチ オブジェクトをサポートしていません; `ppdisp`のパラメーターは `NULL`に設定されます。|  
  
## 解説  
 スクリプト コードはこの呼び出し時に評価されることはありません; なく、プロシージャはスクリプトで後で呼び出すことができる `ppdisp` のメソッドにコンパイルされます。  
  
 このインターフェイスは、インターフェイスを `IActiveScriptParseProcedure` の使用は推奨されません。  `IActiveScriptParseProcedure::ParseProcedureText` のメソッドは、このメソッドに似ていますが、プロシージャ名を指定できます。  すべての状況では、`IActiveScriptParseProcedure::ParseProcedureText` を使用する必要があります。  
  
## 参照  
 [IActiveScriptParseProcedureOld インターフェイス](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)