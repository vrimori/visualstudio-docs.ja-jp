---
title: "IActiveScriptErrorDebug::GetDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptErrorDebug.GetDocumentContext
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptErrorDebug::GetDocumentContext"
ms.assetid: 567601a1-551a-4905-bda1-1f54610174f4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptErrorDebug::GetDocumentContext
このエラーがドキュメントのコンテキストを提供します。  
  
## 構文  
  
```  
HRESULT GetDocumentContext(  
   IDebugDocumentContext**  ppssc  
);  
```  
  
#### パラメーター  
 `ppssc`  
 \[出力\]このエラーのドキュメントのコンテキスト。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 ドキュメントのコンテキストの文字位置のスコープはエラーに対応するすべての文字を含める必要があります。  
  
## 参照  
 [IActiveScriptErrorDebug インターフェイス](../../winscript/reference/iactivescripterrordebug-interface.md)