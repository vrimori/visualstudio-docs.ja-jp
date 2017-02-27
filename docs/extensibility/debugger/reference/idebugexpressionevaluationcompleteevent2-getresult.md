---
title: "IDebugExpressionEvaluationCompleteEvent2::GetResult | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluationCompleteEvent2::GetResult"
helpviewer_keywords: 
  - "IDebugExpressionEvaluationCompleteEvent2::GetResult"
ms.assetid: d9ad3e22-b6b2-421e-9a43-6bb8c70d12a9
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugExpressionEvaluationCompleteEvent2::GetResult
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

式の評価の結果を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetResult(   
   IDebugProperty2** ppResult  
);  
```  
  
```c#  
int GetResult(   
   out IDebugProperty2 ppResult  
);  
```  
  
#### パラメーター  
 `ppResult`  
 \[入力\] 式の評価の結果を表す [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) のオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 返されたオブジェクトは評価された式の値が含まれます。  この値は配列のような複雑な値である可能性がありますが最終結果をユーザーに表示される文字列値または数値であることに注意してください。  
  
## 参照  
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)