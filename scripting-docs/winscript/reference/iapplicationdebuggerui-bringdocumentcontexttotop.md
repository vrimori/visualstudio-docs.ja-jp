---
title: "IApplicationDebuggerUI::BringDocumentContextToTop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebuggerUI.BringDocumentContextToTop
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebuggerUI::BringDocumentContextToTop"
ms.assetid: 7844217d-658b-42af-8d10-2714f4eded20
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebuggerUI::BringDocumentContextToTop
デバッガーのユーザー インターフェイスに特定の文書の先頭にコンテキストを含むウィンドウを取り込み、コンテキストにウィンドウをスクロールします。  
  
## 構文  
  
```  
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### パラメーター  
 `pddc`  
 \[入力\]デバッガーのユーザー インターフェイスの上部に表示されるようにコンテキストを文書化します。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`E_INVALIDARG`|`pddc` で指定されたコンテキストは不明です。|  
  
## 解説  
 このメソッドは、上にデバッガーのユーザー インターフェイスで特定の文書のコンテキストを含むウィンドウを取り込み、コンテキストにウィンドウをスクロールします。  
  
## 参照  
 [IApplicationDebuggerUI インターフェイス](../../winscript/reference/iapplicationdebuggerui-interface.md)