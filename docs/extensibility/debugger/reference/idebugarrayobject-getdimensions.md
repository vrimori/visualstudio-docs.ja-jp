---
title: "IDebugArrayObject::GetDimensions | Microsoft Docs"
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
  - "IDebugArrayObject::GetDimensions"
helpviewer_keywords: 
  - "IDebugArrayObject::GetDimensions メソッド"
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugArrayObject::GetDimensions
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

配列の次元を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```c#  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### パラメーター  
 `dwCount`  
 \[入力\] 取得する次元数。  
  
 `dwDimensions`  
 \[入力出力\] の各次元のサイズが格納された配列。  `dwCount` は `dwDimensions` の配列の最大サイズを指定します。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 多次元配列はインデックスの異なったサイズを設定できます。  たとえば次元配列 `myarray[3][2][6]` はこのメソッドはその順序で `dwDimensions` パラメーターの 3 ビット2 ビットおよび 6 を返します。  
  
## 参照  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)