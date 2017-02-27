---
title: "IDebugExpressionEvaluator2::GetService | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator2::GetService"
  - "GetService"
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionEvaluator2::GetService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

一意の識別子があるサービス オブジェクトを取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetService (  
   GUID        uid,  
   IUnknown ** ppService  
);  
```  
  
```c#  
int GetService (  
   Guid       uid,  
   out object ppService  
);  
```  
  
#### パラメーター  
 `uid`  
 \[入力\] 取得するサービスの一意の識別子。  
  
 `ppService`  
 \[入力\] サービスを表すオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このためサードパーティの式エバリュエーターによって他の式エバリュエーターでサービスを取得するために実装できます。  既定の式エバリュエーターのビジュアライザーのサービスのインターフェイスを取得する場合などにこのメソッドを使用できます。  サードパーティの式エバリュエーターはこのインターフェイスを実装する必要があるのはありません。  
  
## 参照  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)