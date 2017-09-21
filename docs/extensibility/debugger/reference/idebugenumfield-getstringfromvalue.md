---
title: "IDebugEnumField::GetStringFromValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEnumField::GetStringFromValue"
helpviewer_keywords: 
  - "IDebugEnumField::GetStringFromValue メソッド"
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugEnumField::GetStringFromValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドは値を持つ列挙定数の名前を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetStringFromValue(  
   ULONGLONG value,  
   BSTR*     pbstrValue  
);  
```  
  
```c#  
int GetStringFromValue(  
   ulong      value,  
   out string pbstrValue  
);  
```  
  
#### パラメーター  
 `value`  
 \[入力\] 列挙定数の名前を取得する値。  
  
 `pbstrValue`  
 \[入力\] 列挙定数の名前を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の値に関連付けられた名前がない場合戻り `S_FALSE` 場合はエラー コードを返します。  
  
## 解説  
 同じ値に関連付けられた複数の名前がの場合列挙型で定義された名前が返されます。  
  
## 参照  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)