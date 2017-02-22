---
title: "IDebugEnumField::GetValueFromString | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEnumField::GetValueFromString"
helpviewer_keywords: 
  - "IDebugEnumField::GetValueFromString メソッド"
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEnumField::GetValueFromString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

この値が列挙体の定数名に関連付けられたメソッドはを返します。  
  
## 構文  
  
```cpp#  
HRESULT GetValueFromString(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```c#  
int GetValueFromString(  
   string    pszValue,  
   out ulong pValue  
);  
```  
  
#### パラメーター  
 `pszValue`  
 \[入力\] 指定する文字列値を取得する名前。  C\+\+ ではこれはワイド文字列であることに注意してください。  
  
 `pValue`  
 \[出力\] 関連付けられた数値を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の名前は列挙の一部の場合はエラー コードを返します `S_FALSE`。  
  
## 解説  
 このメソッドでは、大文字と小文字が区別されます。  大文字と小文字を区別しない必要があります \(たとえば名前が大文字と小文字を区別しない Visual Basic などの言語で[GetValueFromStringCaseInsensitive](../Topic/IDebugEnumField::GetValueFromStringCaseInsensitive.md)\) を使用します。  
  
## 参照  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromStringCaseInsensitive](../Topic/IDebugEnumField::GetValueFromStringCaseInsensitive.md)