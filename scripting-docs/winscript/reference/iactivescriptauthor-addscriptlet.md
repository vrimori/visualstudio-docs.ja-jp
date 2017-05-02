---
title: "IActiveScriptAuthor::AddScriptlet | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddScriptlet
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddScriptlet"
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptAuthor::AddScriptlet
ルート レベルの `IScriptNode` オブジェクトの子としてスクリプトレット コードを追加します。  ホストでは、スクリプトレットの完全修飾名が 2 回だけレベルがある。  
  
## 構文  
  
```  
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### パラメーター  
 `pszDefaultName`  
 \[入力\]スクリプトレットに関連付ける既定の名前のアドレス。  
  
 `pszCode`  
 \[入力\]スクリプトレットのテキストのアドレス。  
  
 `pszItemName`  
 \[出力\]ホストの完全修飾名スクリプトレットのトップレベルの識別子のバッファーのアドレス。  
  
 `pszSubItemName`  
 \[出力\]ホストの完全修飾名スクリプトレットの 2 番目のレベルの識別子のバッファーのアドレス。  名前に 1 レベルのみの場合に無効にする。  
  
 `pszEventName`  
 \[入力\]スクリプトレットがイベント ハンドラーであるイベント名を含むバッファーのアドレス。  
  
 `pszDelimiter`  
 \[入力\]終わりのスクリプト ブロックの区切り記号のアドレス。  `pszCode` がテキスト ストリームから解析されると、通常ホストは、スクリプト ブロックの末尾を検出するために、区切り記号 \(2 三つの単一引用符など\) を使用します。  区切り記号がスクリプト ブロックの末尾が表示されない場合は無効にするには、このパラメーターをに設定します。  
  
 `dwCookie`  
 \[出力\]ホスト オブジェクトとスクリプトレットを関連付けるためのアプリケーション定義の値。  
  
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