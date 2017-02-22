---
title: "IDebugReference2::GetSize | Microsoft Docs"
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
  - "IDebugReference2::GetSize"
helpviewer_keywords: 
  - "IDebugReference2::GetSize"
ms.assetid: a404ddd9-d940-4513-97cd-f52b8ab6a560
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugReference2::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

サイズが参照値のバイト単位\) を取得します。  将来使用するために予約されています。  
  
## 構文  
  
```cpp#  
HRESULT GetSize (   
   DWORD* pdwSize  
);  
```  
  
```c#  
int GetSize (   
   out uint pdwSize  
);  
```  
  
#### パラメーター  
 `pdwSize`  
 \[入力\] のサイズを参照の値をバイト単位で返します。  
  
## 戻り値  
 常に `E_NOTIMPL` を返します。  
  
## 参照  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)