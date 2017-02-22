---
title: "IDebugArrayField::GetRank | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayField::GetRank"
helpviewer_keywords: 
  - "IDebugArrayField::GetRank メソッド"
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugArrayField::GetRank
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

配列のランクまたはの次元数を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```c#  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### パラメーター  
 `pdwRank`  
 \[入力\] 順位を返します。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 配列のランクは次元数に対応します。  したがってC\+\+ および C\# では多次元配列は配列の配列で次元配列できます \(と常に `GetRank` のメソッドは考慮する 1\)。  で[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]一方多次元配列は異なる方法で処理されこのような配列のランクがディメンション反映します （メソッドおよびメソッドの`GetRank`数の次元数を常に返します）。  
  
## 参照  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)