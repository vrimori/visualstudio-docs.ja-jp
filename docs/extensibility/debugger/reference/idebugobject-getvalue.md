---
title: "IDebugObject::GetValue | Microsoft Docs"
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
  - "IDebugObject::GetValue"
helpviewer_keywords: 
  - "IDebugObject::GetValue メソッド"
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject::GetValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

連続する一連のバイト数としてオブジェクトの値を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```c#  
int GetValue(  
   ref byte[] pValue,   
   uint nSize  
);  
```  
  
#### パラメーター  
 `pValue`  
 \[入力出力\] オブジェクトの値を表す連続する一連のバイト数が格納された配列。  
  
 `nSize`  
 \[入力\] 取得される最大バイト数。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) のメソッドを呼び出して取得できる値のバイト総数を取得します。  
  
## 参照  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)