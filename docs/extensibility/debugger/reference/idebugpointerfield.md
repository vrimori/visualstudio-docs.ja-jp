---
title: "IDebugPointerField | Microsoft Docs"
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
  - "IDebugPointerField"
helpviewer_keywords: 
  - "IDebugPointerField インターフェイス"
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPointerField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスにはポインター型を表します。  
  
## 構文  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## 実装についてのメモ  
 シンボルのプロバイダーはポインターを表すためこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 [GetKind](../Topic/IDebugField::GetKind.md) が `FIELD_TYPE_POINTER` を返す [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) のインターフェイスからこのインターフェイスを取得するに [QueryInterface](/visual-cpp/atl/queryinterface) を使用します。  
  
## Vtable の順序でメソッド  
 `IDebugField` と `IDebugContainerField` のインターフェイスのメソッド以外にもこのインターフェイスには次のメソッドを実行します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|ポインターのターゲットを記述する [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) を返します。|  
  
## 解説  
 C\/C\+\+ では配列表記で使用されるコンテナーです。  たとえば`char *pString` は`pString` に `char` へのポインターの型です。  `pString[3]` に `char` そのコンテナーの 4 番目の要素を参照するポインターであるコンテナーの種類があります。  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [シンボルのプロバイダー インターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)