---
title: "IDebugExpressionEvaluator::SetLocale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator::SetLocale"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator::SetLocale メソッド"
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionEvaluator::SetLocale
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドでは印刷する結果の作成に使用する言語を設定します。  
  
## 構文  
  
```cpp#  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```c#  
int SetLocale(  
   ushort wLangID  
);  
```  
  
#### パラメーター  
 `wLangID`  
 \[出力\] 言語識別子。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 式エバリュエーターでは言語にEE を実行時に \(EE\) 切り替わります必要がありますがこれに何度も呼び出されます。  EE が適切な言語のエラー メッセージの文字列を返すにはこのロケールを使用します。  
  
## 参照  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)