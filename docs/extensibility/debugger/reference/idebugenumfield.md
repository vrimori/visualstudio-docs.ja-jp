---
title: "IDebugEnumField | Microsoft Docs"
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
  - "IDebugEnumField"
helpviewer_keywords: 
  - "IDebugEnumField インターフェイス"
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEnumField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスは列挙型を表します。  
  
## 構文  
  
```  
IDebugEnumField : IDebugContainerField  
```  
  
## 実装についてのメモ  
 シンボルのプロバイダーは列挙型を表すためこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 [GetKind](../Topic/IDebugField::GetKind.md) が `FIELD_TYPE_ENUM` を返す [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) のインターフェイスからこのインターフェイスを取得するに [QueryInterface](/visual-cpp/atl/queryinterface) を使用します。  
  
## VTable の順序でメソッド  
 `IDebugField` と `IDebugContainerField` のインターフェイスのメソッド以外にもこのインターフェイスには次のメソッドを実行します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|この列挙型名を記述する [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) を返します。|  
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|指定された値に関連付けられた列挙定数の名前を返します。|  
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|指定された列挙体の定数名に関連付けられている値を返します|  
|[GetValueFromStringCaseInsensitive](../Topic/IDebugEnumField::GetValueFromStringCaseInsensitive.md)|指定された列挙体の定数名に関連付けられたケースを無視する値を返します。|  
  
## 解説  
 [バインド](../../../extensibility/debugger/reference/idebugbinder-bind.md) の場所に実際にバインドされるのは基になるシンボルです。  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [シンボルのプロバイダー インターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [バインド](../../../extensibility/debugger/reference/idebugbinder-bind.md)