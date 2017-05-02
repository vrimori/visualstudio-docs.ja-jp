---
title: "IDebugDocumentTextEvents::onUpdateDocumentAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextEvents.onUpdateDocumentAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentTextEvents::onUpdateDocumentAttributes"
ms.assetid: 48fa909c-14c2-4ca4-af86-a5809c72dd39
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextEvents::onUpdateDocumentAttributes
ドキュメントの属性が変更されたことを示します。  
  
## 構文  
  
```  
HRESULT onUpdateDocumentAttributes(  
   TEXT_DOC_ATTR  textdocattr  
);  
```  
  
#### パラメーター  
 `textdocattr`  
 \[入力\]新しいドキュメントの属性。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、文書の属性が変更されたことを示します。  
  
## 参照  
 [IDebugDocumentTextEvents インターフェイス](../../winscript/reference/idebugdocumenttextevents-interface.md)   
 [TEXT\_DOC\_ATTR 定数](../../winscript/reference/text-doc-attr-constants.md)