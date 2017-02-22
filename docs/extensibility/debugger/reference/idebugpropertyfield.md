---
title: "IDebugPropertyField | Microsoft Docs"
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
  - "IDebugPropertyField"
helpviewer_keywords: 
  - "IDebugPropertyField インターフェイス"
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPropertyField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはプロパティを取得および設定を行うことができる関数が用意されています。  
  
## 構文  
  
```  
IDebugPropertyField : IDebugContainerField  
```  
  
## 実装についてのメモ  
 シンボルはプロバイダーでこのインターフェイスを実装するオブジェクト [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 実行します。  このインターフェイスはクラスのプロパティの概念をサポートする特化したクラスです。  
  
## 呼び出し元のメモ  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) のインターフェイスからこのインターフェイスを取得するに [QueryInterface](/visual-cpp/atl/queryinterface) を [GetKind](../Topic/IDebugField::GetKind.md) のメソッド `FIELD_KIND_PROP` 使用します。  
  
## Vtable の順序でメソッド  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) と [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) のインターフェイスのメソッド以外にもこのインターフェイスには次のメソッドを実行します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|プロパティを取得するメソッドを取得します。|  
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|プロパティを設定するメソッドを取得します。|  
  
## 解説  
 プロパティはマネージ コードの概念に変数として扱うメソッドを表します。  プロパティはアンマネージ C\+\+ ではありません。  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [シンボルのプロバイダー インターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)