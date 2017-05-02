---
title: "IDebugDocumentTextEvents::onUpdateTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextEvents.onUpdateTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentTextEvents::onUpdateTextAttributes"
ms.assetid: 24a6d409-3137-4a7a-ac24-0955c109902f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextEvents::onUpdateTextAttributes
基になる文字位置の範囲に関連付けられたテキスト属性が変更されたことを示します。  
  
## 構文  
  
```  
HRESULT onUpdateTextAttributes(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToUpdate  
);  
```  
  
#### パラメーター  
 `cCharacterPosition`  
 \[入力\]属性を変更した最初の文字の位置。  
  
 `cNumToUpdate`  
 \[入力\]範囲の文字数。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、基になる文字位置の範囲に関連付けられたテキスト属性が変更されたことを示します。  
  
## 参照  
 [IDebugDocumentTextEvents インターフェイス](../../winscript/reference/idebugdocumenttextevents-interface.md)