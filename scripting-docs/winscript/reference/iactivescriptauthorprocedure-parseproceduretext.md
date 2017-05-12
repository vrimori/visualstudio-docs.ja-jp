---
title: "IActiveScriptAuthorProcedure::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthorProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthorProcedure::ParseProcedureText"
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthorProcedure::ParseProcedureText
プロシージャ コードを分析し、スクリプト エンジンの作成手順のコードにテキストを追加し、プロシージャ コードに対応する `IScriptEntry` のオブジェクトを作成します。  
  
## 構文  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### パラメーター  
 `pszCode`  
 \[入力\]分析するスクリプトのテキスト。  
  
 `pszFormalParams`  
 \[入力\]プロシージャの仮パラメーター名のアドレス。  パラメーター名はエンジンの作成スクリプトの適切な区切り記号で区切る必要があります。  名前はかっこで囲む必要ではありません。  
  
 `pszProcedureName`  
 \[入力\]解析されるプロシージャ名のアドレス。  
  
 `pszItemName`  
 \[入力\] `IScriptEntry` のオブジェクトに関連付けられた項目の名前を含むバッファーのアドレス。  
  
 `pszDelimiter`  
 \[入力\]終わりのスクリプト ブロックの区切り記号のアドレス。  `pszCode` がテキスト ストリームから解析されると、通常ホストは、スクリプト ブロックの末尾を検出するために、区切り記号 \(2 三つの単一引用符など\) を使用します。  スクリプト ブロックの終わりを示す区切り記号がない場合は無効にするには、このパラメーターをに設定します。  
  
 `dwCookie`  
 \[入力\] `IScriptEntry` の新しいオブジェクトに関連付けられたアプリケーション定義の値。  
  
 `dwFlags`  
 \[入力\] 使われません。  
  
 `pdispFor`  
 \[入力\] 使われません。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] の現在のエンジンはこのメソッドを実装しません。  
  
## 参照  
 [IActiveScriptAuthorProcedure インターフェイス](../../winscript/reference/iactivescriptauthorprocedure-interface.md)