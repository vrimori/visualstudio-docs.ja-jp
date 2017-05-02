---
title: "IActiveScriptSite::GetDocVersionString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetDocVersionString
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetDocVersionString"
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetDocVersionString
現在のドキュメントのバージョンを区別するホスト定義の文字列を取得します。  関連するドキュメントに Windows スクリプトのスコープ外で HTML ページ \(の場合は\) 変更した場合は、メモ帳編集すると、スクリプト エンジンは、再コンパイルを強制的に実行する保持された状態とともにスクリプトが読み込まれたときにこれを保存できます。  
  
## 構文  
  
```  
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### パラメーター  
 `pstrVersionString`  
 \[出力\]ホスト定義されたドキュメントのバージョン文字列のアドレス。  
  
## 戻り値  
 このメソッドがサポートされていない場合、または `E_NOTIMPL` が成功した場合 `S_OK` 返します。  
  
## 解説  
 `E_NOTIMPL` がを返した場合、スクリプト エンジンは、スクリプトをドキュメントと ASPX することを想定する必要があります。  
  
## 参照  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)