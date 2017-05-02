---
title: "IActiveScriptAuthor::IsCommitChar | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.IsCommitChar
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::IsCommitChar"
ms.assetid: 7857c6f9-61e6-41e5-8e01-f56588c10421
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IActiveScriptAuthor::IsCommitChar
特定の文字は、アプリケーションによってステートメント入力候補のコミットメントをトリガーするかどうかを示す値を返します。  
  
## 構文  
  
```  
HRESULT IsCommitChar(  
   OLECHAR    ch,  
   BOOL       *pfcommit  
);  
```  
  
#### パラメーター  
 `ch`  
 \[入力\]テストする文字。  
  
 `pfcommit`  
 \[入力\]文字がコミットの場合は `True` ; それ以外 `False`。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
  
## 参照  
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)