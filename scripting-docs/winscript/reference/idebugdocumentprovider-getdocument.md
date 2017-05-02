---
title: "IDebugDocumentProvider::GetDocument | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentProvider.GetDocument
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentProvider::GetDocument"
ms.assetid: da67dab0-778a-4dab-8ca3-055ee7a4f141
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentProvider::GetDocument
既にあるドキュメントをインスタンス化します。  
  
## 構文  
  
```  
HRESULT GetDocument(  
   IDebugDocument**  ppssd  
);  
```  
  
#### パラメーター  
 `ppssd`  
 \[入力\]ドキュメントに対応するデバッグのドキュメント。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、既にあるドキュメントをインスタンス化します。  
  
## 参照  
 [IDebugDocumentProvider インターフェイス](../../winscript/reference/idebugdocumentprovider-interface.md)