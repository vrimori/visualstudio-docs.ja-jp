---
title: "IDebugObject2::GetICorDebugValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::GetICorDebugValue"
helpviewer_keywords: 
  - "IDebugObject2::GetICorDebugValue メソッド"
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugObject2::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

マネージ コードを表すオブジェクトの値をこのオブジェクトに関連付けられているを取得します。  
  
## 構文  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```c#  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### パラメーター  
 `ppUnk`  
 \[出力\] この `IUnknown` のエイリアスを表すインターフェイス。  このインターフェイスは `ICorDebugValue` のインターフェイスを照会できます。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 `ICorDebugValue` のオブジェクトが値を表す共通言語ランタイムのインターフェイスです。  
  
## 参照  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)