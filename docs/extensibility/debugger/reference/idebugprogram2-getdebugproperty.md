---
title: "IDebugProgram2::GetDebugProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetDebugProperty"
helpviewer_keywords: 
  - "IDebugProgram2::GetDebugProperty"
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::GetDebugProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プログラムのプロパティを取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetDebugProperty(   
   IDebugProperty2** ppProperty  
);  
```  
  
```c#  
int GetDebugProperty(   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### パラメーター  
 `ppProperty`  
 \[入力\] プログラムのプロパティを表す [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) のオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドによって返されるプロパティはプログラムに固有です。  複数のプロパティを返すプログラムの場合はこのメソッドによって返される [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) オブジェクトの追加のプロパティと [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) のメソッドをすべてのプロパティの一覧を呼び出すことのコンテナーです。  
  
 プログラムは `IDebugProperty2` のインターフェイスを通じて記述できる追加のプロパティの数と型を公開する場合があります。  IDE では一般的なプロパティ ブラウザーのユーザー インターフェイスを通じてプログラムの追加プロパティを表示する場合があります。  
  
## 参照  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)