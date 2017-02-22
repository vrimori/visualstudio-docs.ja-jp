---
title: "IDebugArrayObject::GetCount | Microsoft Docs"
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
  - "IDebugArrayObject::GetCount"
helpviewer_keywords: 
  - "IDebugArrayObject::GetCount メソッド"
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugArrayObject::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

配列の要素の数を取得します。  
  
## 構文  
  
```  
[C++]  
HRESULT GetCount(   
   DWORD* pdwElements  
);  
```  
  
```  
[C#]  
int GetCount(  
   out uint pdwElements  
);  
```  
  
#### パラメーター  
 `pdwElements`  
 \[入力\] 数を返します。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドは次元配列として配列オブジェクトが多次元配列でも配列オブジェクトの要素をすべて表示されます。  たとえば配列 `myarray[3][2][6]` はこのメソッドは `pdwElements` パラメーターの 36 を返します。  個々の要素を一つずつ取得するために [GetElement](../Topic/IDebugArrayObject::GetElement.md) のメソッドを使用します。  
  
## 参照  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)