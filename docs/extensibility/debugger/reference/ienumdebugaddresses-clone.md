---
title: "IEnumDebugAddresses::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugAddresses::Clone"
helpviewer_keywords: 
  - "IEnumDebugAddresses::Clone メソッド"
ms.assetid: 71189a00-34eb-4c71-b96e-8bd6e70c6966
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IEnumDebugAddresses::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

メソッドは現在の列挙体のコピーを個々のオブジェクトとしてこの。  
  
## 構文  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugAddresses** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugAddresses ppEnum  
);  
```  
  
#### パラメーター  
 `ppEnum`  
 \[入力\] 個々のオブジェクトとしてこの列挙体のコピーを返します。  
  
## プロパティ値\/戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドが呼び出されたときに列挙値のコピー元と同じ状態があります。  ただしコピー元の状態とは別にそれぞれ変更できます。  
  
## 参照  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)