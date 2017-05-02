---
title: "IDebugDocumentHelper::SetLongName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.SetLongName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::SetLongName"
ms.assetid: b6199e5d-9b54-43a2-9775-214b8d022607
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::SetLongName
ドキュメントの長い名前を設定します。  
  
## 構文  
  
```  
HRESULT SetLongName(  
   LPCOLESTR  pszLongName  
);  
```  
  
#### パラメーター  
 `pszLongName`  
 \[入力\]ドキュメントの長い名前を含む文字列が null で終了します。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、文書の新しい長い名前を設定します。  
  
## 参照  
 [IDebugDocumentHelper インターフェイス](../../winscript/reference/idebugdocumenthelper-interface.md)