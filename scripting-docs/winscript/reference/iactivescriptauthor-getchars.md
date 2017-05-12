---
title: "IActiveScriptAuthor::GetChars | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetChars
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetChars"
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IActiveScriptAuthor::GetChars
要求された実行コンテキストの終了文字のセットを返します。  
  
## 構文  
  
```  
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### パラメーター  
 `fRequestedList`  
 \[入力\]要求された実行コンテキスト。  
  
|定数|値|説明|  
|--------|-------|--------|  
|SCRIPT\_CMPL\_ENUM\_TRIGGER|0x0001|左側の列挙体を要求します。|  
|SCRIPT\_CMPL\_MEMBER\_TRIGGER|0x0002|メンバーの実行コンテキストを要求します。|  
|SCRIPT\_CMPL\_PARAM\_TRIGGER|0x0003|パラメーター リストが必要です。|  
|SCRIPT\_CMPL\_COMMIT|0x0004|パラメーター リストの完了が必要です。|  
  
 `pbstrChars`  
 \[入力\]要求された実行コンテキストに対応する文字。  
  
|`fRequestedList` パラメーター|返される文字|  
|-----------------------------|------------|  
|SCRIPT\_CMPL\_ENUM\_TRIGGER|"."|  
|SCRIPT\_CMPL\_MEMBER\_TRIGGER|「\=」|  
|SCRIPT\_CMPL\_PARAM\_TRIGGER|\(「」、|  
|SCRIPT\_CMPL\_COMMIT|「 \(\) 」|  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
  
## 参照  
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)