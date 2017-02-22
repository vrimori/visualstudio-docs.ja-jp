---
title: "IDebugClassField | Microsoft Docs"
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
  - "IDebugClassField"
helpviewer_keywords: 
  - "IDebugClassField インターフェイス"
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugClassField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスは型としてクラスを表します。  
  
## 構文  
  
```  
IDebugClassField : IDebugContainerField  
```  
  
## 実装についてのメモ  
 シンボルのは同じオブジェクト プロバイダーでこのインターフェイスを実装する [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) のインターフェイスを実装します。  このインターフェイスはクラス型を表す特化したクラスです。  
  
## 呼び出し元のメモ  
 いくつかのインターフェイスに [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) と [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) を含めこのインターフェイスを返すことができるメソッドがあります。  また[GetKind](../Topic/IDebugField::GetKind.md) のメソッドはフラグ `FIELD_TYPE_CLASS`[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) のインターフェイスからこのインターフェイスを取得するに [QueryInterface](/visual-cpp/atl/queryinterface) を使用できます。  
  
## Vtable の順序でメソッド  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) と [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) のインターフェイスのメソッド以外にもこのインターフェイスは次を実行します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[EnumBaseClasses](../Topic/IDebugClassField::EnumBaseClasses.md)|このクラスの基本クラスの列挙子を作成します。|  
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|特定のインターフェイスが定義されているかどうかを判定します。|  
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|このクラスの入れ子になったクラスの列挙子を作成します。|  
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|このクラスを囲むクラスを取得します。|  
|[EnumInterfacesImplemented](../Topic/IDebugClassField::EnumInterfacesImplemented.md)|このクラスによって実装されるインターフェイスの列挙子を作成します。|  
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|このクラスのコンストラクターの列挙子を作成します。|  
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|既定のインデクサーの名前を取得します。|  
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|このクラスの入れ子になった列挙子の列挙子を作成します。|  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [シンボルのプロバイダー インターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)