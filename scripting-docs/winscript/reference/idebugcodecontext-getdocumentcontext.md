---
title: "IDebugCodeContext::GetDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugCodeContext.GetDocumentContext
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugCodeContext::GetDocumentContext"
ms.assetid: 9fe17b65-3a8c-4d21-9b66-0e4ff303af72
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCodeContext::GetDocumentContext
このコード コンテキストに関連付けられているドキュメントのコンテキストを返します。  
  
## 構文  
  
```  
HRESULT GetDocumentContext(  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### パラメーター  
 `ppsc`  
 \[出力\]このコード コンテキストに関連付けられているドキュメントのコンテキスト。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 テキスト ドキュメントでは、文字位置のスコープは、全体のステートメントのテキストを含める必要があります。  これは、デバッガーの IDE が現在のソース ステートメントを強調表示できます。  
  
## 参照  
 [IDebugCodeContext インターフェイス](../../winscript/reference/idebugcodecontext-interface.md)