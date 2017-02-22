---
title: "IEnumDebugPropertyInfo2::Clone | Microsoft Docs"
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
  - "IEnumDebugPropertyInfo2::Clone"
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo2::Clone"
ms.assetid: 0ede1667-1071-4aa4-b887-260ea103d724
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugPropertyInfo2::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

個々のオブジェクトとして現在の列挙体のコピーを返します。  
  
## 構文  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### パラメーター  
 `ppEnum`  
 \[入力\] 個々のオブジェクトとしてこの列挙体のコピーを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドが呼び出されたときに列挙値のコピー元と同じ状態があります。  ただしコピー元の状態とは別にそれぞれ変更できます。  
  
## 参照  
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)