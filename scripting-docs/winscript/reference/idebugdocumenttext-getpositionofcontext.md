---
title: "IDebugDocumentText::GetPositionOfContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetPositionOfContext
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetPositionOfContext"
ms.assetid: 90fec730-c3fb-45fb-92ef-05ecc90dca38
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetPositionOfContext
ドキュメントのコンテキストに対応する文字位置の範囲を返します。  
  
## 構文  
  
```  
HRESULT GetPositionOfContext(  
   IDebugDocumentContext*  psc,  
   ULONG*                  pcCharacterPosition,  
   ULONG*                  cNumChars  
);  
```  
  
#### パラメーター  
 `psc`  
 \[入力\]ドキュメントのコンテキスト オブジェクト。  
  
 `pcCharacterPosition`  
 \[入力\]文字位置の範囲の開始位置。  
  
 `cNumChars`  
 \[入力\]範囲の文字数。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドに渡されたドキュメントのコンテキストでこのドキュメントに関連付ける必要があります。  
  
## 参照  
 [IDebugDocumentText インターフェイス](../../winscript/reference/idebugdocumenttext-interface.md)