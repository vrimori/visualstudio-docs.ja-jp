---
title: "IEnumDebugErrorBreakpoints2::Clone | Microsoft Docs"
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
  - "IEnumDebugErrorBreakpoints2::Clone"
helpviewer_keywords: 
  - "IEnumDebugErrorBreakpoints2::Clone"
ms.assetid: f6fb4985-8dd6-4a9b-98e0-15dbc64cc9ec
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugErrorBreakpoints2::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

個々のオブジェクトとして現在の列挙体のコピーを返します。  
  
## 構文  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugErrorBreakpoints2** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugErrorBreakpoints2 ppEnum  
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
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)