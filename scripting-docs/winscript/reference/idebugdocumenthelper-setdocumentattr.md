---
title: "IDebugDocumentHelper::SetDocumentAttr | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.SetDocumentAttr
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::SetDocumentAttr"
ms.assetid: bd7ffdbd-de51-477d-bd3f-760db020fe70
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::SetDocumentAttr
このドキュメントの属性を設定します。  
  
## 構文  
  
```  
HRESULT SetDocumentAttr(  
   TEXT_DOC_ATTR  pszAttributes  
);  
```  
  
#### パラメーター  
 `pszAttributes`  
 \[入力\]ドキュメントに適用する属性。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、このドキュメントの属性を設定します。  
  
## 参照  
 [IDebugDocumentHelper インターフェイス](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT\_DOC\_ATTR 定数](../../winscript/reference/text-doc-attr-constants.md)