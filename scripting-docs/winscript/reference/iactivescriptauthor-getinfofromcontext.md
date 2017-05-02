---
title: "IActiveScriptAuthor::GetInfoFromContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetInfoFromContext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetInfoFromContext"
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthor::GetInfoFromContext
戻り値は情報を入力し、コード ブロックの特定の文字の位置を固定します。  これは、メンバーの IntelliSense、グローバル リスト、およびパラメーターのヒントについて説明します。  
  
## 構文  
  
```  
HRESULT GetInfoFromContext(  
   LPCOLESTR  pszCode,  
   ULONG      cchCode,  
   ULONG      ichCurrentPosition,  
   DWORD      dwListTypesRequested,  
   DWORD      *pdwListTypesProvided,  
   ULONG      *pichListAnchorPosition,  
   ULONG      *pichFuncAnchorPosition,  
   MEMBERID   *pmemid,  
   LONG       *piCurrentParameter,  
   IUnknown   **ppunk  
);  
```  
  
#### パラメーター  
 `pszCode`  
 \[入力\]情報の生成に使用されたコード ブロックの文字列のアドレスが発生します。  
  
 `cchCode`  
 \[入力\]コード ブロックの長さ。  
  
 `ichCurrentPosition`  
 \[入力\]ブロックの先頭に関連する文字の位置。  
  
 `dwListTypesRequested`  
 \[入力\]要求されたリストの種類。  次の値の組み合わせがあります:  
  
|定数|値|説明|  
|--------|-------|--------|  
|SCRIPT\_CMPL\_NOLIST|0x0000|リストはありません。|  
|SCRIPT\_CMPL\_MEMBERLIST|0x0001|メンバーの一覧。|  
|SCRIPT\_CMPL\_ENUMLIST|0x0002|enum のリスト。|  
|SCRIPT\_CMPL\_PARAMLIST|0x0004|呼び出しのメソッドのパラメーター リスト。|  
|SCRIPT\_CMPL\_GLOBALLIST|0x0008|グローバル リスト。|  
  
 SCRIPT\_CMPL\_GLOBALLIST の型は他の入力候補項目を使用するか、演算子で結合できる既定の入力候補項目として扱われます。  エンジンの作成スクリプトが最初に他のコンプリート リスト項目の型情報を設定しようとします。  失敗した場合、SCRIPT\_CMPL\_GLOBALLIST のエンジンがに読み込まれます。  
  
 `pdwListTypesProvided`  
 \[入力\]指定されたリストの型。  
  
 `pichListAnchorPosition`  
 \[出力\]現在位置を含むコンテキストの開始インデックス。  開始インデックスは、ブロックの先頭を基準にします。  
  
 これは `dwListTypesRequested` が SCRIPT\_CMPL\_MEMBERLIST、SCRIPT\_CMPL\_ENUMLIST、または SCRIPT\_CMPL\_GLOBALLIST が含まれている場合にのみ表示されます。  他の要求されたリストの型の場合、結果は未定義になります。  
  
 `pichFuncAnchorPosition`  
 \[出力\]現在位置を含む関数呼び出しの開始インデックス。  開始インデックスは、ブロックの先頭を基準にします。  
  
 これは現在位置を含むコンテキストが関数呼び出しの場合にのみ、`dwListTypesRequested` が SCRIPT\_CMPL\_PARAMLIST が含まれている場合に表示されます。  それ以外の場合、結果は未定義です。  
  
 `pmemid`  
 \[入力\] `IProvideMultipleClassInfo``ppunk` のによって定義された関数の MEMBERID、パラメーターの型。  
  
 これは `dwListTypesRequested` が SCRIPT\_CMPL\_PARAMLIST が含まれている場合にのみ表示されます。  
  
 `piCurrentParameter`  
 \[出力\]現在位置を含むパラメーターのインデックス。  現在位置が関数名にある場合、\-1 が返されます。  
  
 `piCurrentParameter` の値は `dwListTypesRequested` が SCRIPT\_CMPL\_PARAMLIST が含まれている場合にのみ表示されます。  
  
 `ppunk`  
 `IProvideMultipleClassInfo` のオブジェクトの形式で提供される型の情報。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
  
## 参照  
 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideMultipleClassInfo>   
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)