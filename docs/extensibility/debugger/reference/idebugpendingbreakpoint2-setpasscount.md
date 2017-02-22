---
title: "IDebugPendingBreakpoint2::SetPassCount | Microsoft Docs"
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
  - "IDebugPendingBreakpoint2::SetPassCount"
helpviewer_keywords: 
  - "SetPassCount メソッド"
  - "IDebugPendingBreakpoint2::SetPassCount メソッド"
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPendingBreakpoint2::SetPassCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

パスの数が保留中のブレークポイントに関連付けられている変更または設定します。  
  
## 構文  
  
```cpp#  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```c#  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### パラメーター  
 `bpPassCount`  
 \[入力\] パスの数を含む [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) の構造体。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  ブレークポイントが削除された `E_BP_DELETED` を返します。  
  
## 解説  
 保留中のブレークポイントが関連付けられているパスの数は失われます。  この保留中のブレークポイントからバインドされたすべてのブレークポイントは `bpPassCount` のパラメーターにパスの数を設定するために呼び出されます。  
  
## 参照  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)