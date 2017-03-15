---
title: "IEEVisualizerServiceProvider::CreateVisualizerService | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerServiceProvider::CreateVisualizerService"
helpviewer_keywords: 
  - "IEEVisualizerServiceProvider::CreateVisualizerService メソッド"
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEEVisualizerServiceProvider::CreateVisualizerService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドはビジュアライザーのサービスを作成します。  
  
## 構文  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```c#  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
);  
```  
  
#### パラメーター  
 `binder`  
 \[入力\] [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) のオブジェクトは [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) に渡されました。  
  
 `pSymProv`  
 \[入力\] [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) のオブジェクトは `IDebugParsedExpression::EvaluateSync` に渡されました。  
  
 `pAddress`  
 \[入力\] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) のオブジェクトは `IDebugParsedExression::EvaluateSync` に渡されました。  
  
 `dataProvider`  
 \[入力\] [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) インターフェイス \(式エバリュエーターが提供するもの\) を実装するオブジェクト。  
  
 `ppService`  
 \[入力\] 作成されたサービス。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 `binder` `pSymProv` と `pAddress` のすべてのパラメーターはメソッドを `IDebugParsedExpression::EvaluateSync` に渡されました。  `CreateVisualizerService` は型のビジュアライザーの式エバリュエーターの一部として `IDebugParsedExpression::EvaluateSync` からのみ呼び出すことができます。  
  
## 参照  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)