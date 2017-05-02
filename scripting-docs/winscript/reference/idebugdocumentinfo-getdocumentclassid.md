---
title: "IDebugDocumentInfo::GetDocumentClassId | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentInfo.GetDocumentClassId
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentInfo::GetDocumentClassId"
ms.assetid: 3b858794-2c0c-42ba-b98c-cd820ebace20
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentInfo::GetDocumentClassId
ドキュメントの種類を識別する `CLSID` を返します。  
  
## 構文  
  
```  
HRESULT GetDocumentClassId(  
   CLSID*  pclsidDocument  
);  
```  
  
#### パラメーター  
 `pclsidDocument`  
 \[入力\]ドキュメントの種類を識別する、`CLSID`。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、デバッガーの IDE がこのドキュメントのカスタム ビューアーをホストするようにします。  
  
 ドキュメントに参照できるデータがない場合は、`pclsidDocument` の戻り値は `CLSID_NULL`です。  
  
## 参照  
 [IDebugDocumentInfo インターフェイス](../../winscript/reference/idebugdocumentinfo-interface.md)