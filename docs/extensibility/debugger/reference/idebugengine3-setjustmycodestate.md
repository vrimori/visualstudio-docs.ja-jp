---
title: "IDebugEngine3::SetJustMyCodeState | Microsoft Docs"
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
  - "IDebugEngine3::SetJustMyCodeState"
helpviewer_keywords: 
  - "IDebugEngine3::SetJustMyCodeState"
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine3::SetJustMyCodeState
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドはJustMyCode 状態の情報に関するデバッグ エンジンを示します。  
  
## 構文  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```c#  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### パラメーター  
 `fUpdate`  
 \[出力\] \(ゼロ\)`TRUE` 現在の情報をすべての情報が設定されている \(何も前に無視\) リセットするに更新するには \(`FALSE`\)。  
  
 `dwModules`  
 \[入力\] `rgJMCSpec.` 情報構造体の数  
  
 `rgJMCSpec`  
 \[入力\] 使用する [JMC\_CODE\_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) の構造体の配列。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 JustMyCode はソース・コードにそのシステム コードで使用可能な場合はユーザー コードと同じなシステムなどの中間コードを無視するに属するコードのみのデバッグの概念です。  
  
## 参照  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC\_CODE\_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)