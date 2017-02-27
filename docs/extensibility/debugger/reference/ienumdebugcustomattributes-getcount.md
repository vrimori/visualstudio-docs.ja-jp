---
title: "IEnumDebugCustomAttributes::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumCustomAttributes::GetCount"
helpviewer_keywords: 
  - "IEnumDebugCustomAttributes::GetCount"
ms.assetid: fafe826f-4ebf-4572-b2a3-d5dd2916c12f
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugCustomAttributes::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

列挙子のカスタム属性の数を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetCount(   
   ULONG* pcelt  
);  
```  
  
```c#  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### パラメーター  
 `pcelt`  
 \[入力\] 列挙体の要素数を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドは実行される `Next``Clone``Skip` と `Reset` のニーズを指定する通常の COM 列挙インターフェイスの一部ではありません。  
  
## 参照  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)