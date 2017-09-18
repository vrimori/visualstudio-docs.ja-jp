---
title: "IDebugMethodField::GetGlobalContainer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::GetGlobalContainer"
helpviewer_keywords: 
  - "IDebugMethodField::GetGlobalContainer メソッド"
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugMethodField::GetGlobalContainer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

メソッドのグローバルなコンテナーを取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetGlobalContainer(  
   IDebugClassField** ppClass  
);  
```  
  
```c#  
int GetGlobalContainer(  
   out IDebugClassField ppClass  
);  
```  
  
#### パラメーター  
 `ppClass`  
 \[出力\] このメソッドが定義されているモジュールを表す [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) を返します。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 返されたオブジェクトはモジュール全体を表し人為的なオブジェクトでありつまりモジュール自体は実際のクラスを備えなくて `IDebugClassField` のオブジェクトで表すことができます。列挙し検出されるとしてモジュールのさまざまな要素ができます。  
  
## 参照  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)