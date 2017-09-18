---
title: "IDebugReference2::Compare | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2::Compare"
helpviewer_keywords: 
  - "IDebugReference2::Compare"
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugReference2::Compare
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

他の状態への 1 回の参照を比較します。  将来使用するために予約されています。  
  
## 構文  
  
```cpp#  
HRESULT Compare (   
   REFERENCE_COMPARE dwCompare,  
   IDebugReference2* pReference  
);  
```  
  
```c#  
int Compare (   
   enum_REFERENCE_COMPARE dwCompare,  
   IDebugReference2       pReference  
);  
```  
  
#### パラメーター  
 `dwCompare`  
 \[入力\] 比較演算 \(等号を指定する [REFERENCE\_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) の列挙体からの値" 未満 "" より大きい。  
  
 `pReference`  
 \[入力\] [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) を表すオブジェクトと比較する参照。  
  
## 戻り値  
 常に `E_NOTIMPL` を返します。  
  
## 参照  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [REFERENCE\_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)