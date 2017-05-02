---
title: "IDebugDocumentHelper::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.Attach
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::Attach"
ms.assetid: 834f23a9-716d-44df-b23c-d1bf6da60e79
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::Attach
ドキュメント ツリーにこのドキュメントを追加します。  
  
## 構文  
  
```  
HRESULT Attach(  
   IDebugDocumentHelper*  pddhParent  
);  
```  
  
#### パラメーター  
 `pddhParent`  
 \[入力\]ドキュメントに追加されたドキュメント ツリー。  NULL でもかまいません。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、親として `pddhParent` を使用してドキュメント ツリーにこのドキュメントを追加します。  `pddhParent` が `NULL`場合、このドキュメントはトップレベル ドキュメントです。  
  
## 参照  
 [IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)   
 [IDebugDocumentHelper インターフェイス](../../winscript/reference/idebugdocumenthelper-interface.md)