---
title: "IDebugMethodField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField"
helpviewer_keywords: 
  - "IDebugMethodField インターフェイス"
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugMethodField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはメソッドについて説明します。  
  
## 構文  
  
```  
IDebugMethodField : IDebugContainerField  
```  
  
## 実装についてのメモ  
 シンボルのは同じオブジェクト プロバイダーでこのインターフェイスを実装する [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) のインターフェイスを実装します。  このインターフェイスはメソッドを示す特化したクラスです。  
  
## 呼び出し元のメモ  
 [GetKind](../Topic/IDebugField::GetKind.md) が `FIELD_TYPE_METHOD` を返す [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) のインターフェイスからこのインターフェイスを取得するに [QueryInterface](/visual-cpp/atl/queryinterface) を使用します。  またメソッド[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md) と [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md) のすべてを返します `IDebugMethodField` のインターフェイス。  
  
## Vtable の順序でメソッド  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) と [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) のインターフェイスのメソッド以外にもこのインターフェイスには次のメソッドを実行します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|メソッドのパラメーターの列挙子を作成します。|  
|[Get\-](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|含むオブジェクトの 「」ポインターにメソッドを取得します。|  
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|メソッドのすべてのローカル変数の列挙子を作成します。|  
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|メソッドの選択されたローカル変数の列挙子を作成します。|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|特定のカスタム属性が定義されているかどうかを判定します。|  
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|メソッドの静的ローカル変数の列挙子を作成します。|  
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|メソッドのグローバルなコンテナーを取得します。|  
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|メソッドを呼び出すために必要な各引数の型の列挙子を作成します。|  
  
## 解説  
 メソッドはパラメーターまたはローカル変数を含めることができます。  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [シンボルのプロバイダー インターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)