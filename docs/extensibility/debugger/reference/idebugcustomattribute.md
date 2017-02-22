---
title: "IDebugCustomAttribute | Microsoft Docs"
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
  - "IDebugCustomAttribute"
helpviewer_keywords: 
  - "IDebugCustomAttribute インターフェイス"
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCustomAttribute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはカスタム属性を表し属性の名前および親クラス型を指定できます。  
  
## 構文  
  
```  
IDebugCustomAttribute : IUnknown  
```  
  
## 実装についてのメモ  
 シンボルのプロバイダーはシンボルに関連付けられたカスタム属性をサポートするにはこのインターフェイスを実装します。  これは通常各オブジェクトを独自に実装されます。  
  
## 呼び出し元のメモ  
 [次へ](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) の呼び出しはこのインターフェイスを返します。  [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) のメソッドの呼び出し [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) のインターフェイス。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugCustomAttribute` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetParentField](../Topic/IDebugCustomAttribute::GetParentField.md)|現在の属性がアタッチされているフィールドを取得します。|  
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|カスタム属性クラス型を取得します。|  
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|カスタム属性の名前を取得します。|  
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|バイトの BLOB として属性情報を取得します。|  
  
## 解説  
 カスタム属性は特定のクラスまたはメソッドに関連付けられたカスタムのメタデータを指定する C\# の構造体です。  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [シンボルのプロバイダー インターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)