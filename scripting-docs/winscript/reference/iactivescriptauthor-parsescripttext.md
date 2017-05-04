---
title: "IActiveScriptAuthor::ParseScriptText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.ParseScriptText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::ParseScriptText"
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthor::ParseScriptText
分析はテキストのスクリプトを記述して、スクリプト エンジンの作成にテキストを追加し、スクリプト ブロックに対応する `IScriptEntry` のオブジェクトを作成します。  
  
## 構文  
  
```  
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### パラメーター  
 `pszCode`  
 \[入力\]分析するスクリプトのテキスト。  
  
 `pszItemName`  
 \[入力\]スクリプト ブロックに関連付けられた項目の名前を含むバッファーのアドレス。  
  
 `pszDelimiter`  
 \[入力\]終わりのスクリプト ブロックの区切り記号のアドレス。  `pszCode` がテキスト ストリームから解析されると、通常ホストは、スクリプト ブロックの末尾を検出するために、区切り記号 \(2 三つの単一引用符など\) を使用します。  スクリプト ブロックの末尾を識別する区切り記号がない場合は無効にするには、このパラメーターをに設定します。  
  
 `dwCookie`  
 \[入力\] `IScriptEntry` の新しいオブジェクトに関連付けられたアプリケーション定義の値。  
  
 `dwFlags`  
 \[入力\] 使われません。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
  
## 参照  
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)