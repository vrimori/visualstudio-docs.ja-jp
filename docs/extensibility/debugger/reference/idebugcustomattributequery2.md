---
title: "IDebugCustomAttributeQuery2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomAttributeQuery2"
helpviewer_keywords: 
  - "IDebugCustomAttributeQuery インターフェイス"
  - "IDebugCustomAttributeQuery2 インターフェイス"
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugCustomAttributeQuery2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このフィールドのカスタム属性の有無を確認しの場合属性情報を返します。  
  
## 構文  
  
```  
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery  
```  
  
## 実装についてのメモ  
 シンボルのプロバイダーはカスタム属性をサポートするために同じオブジェクトこのインターフェイスを実装する [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 実行します。  
  
## 呼び出し元のメモ  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) のインターフェイスからこのインターフェイスを取得するに [QueryInterface](/visual-cpp/atl/queryinterface) を使用します。  
  
## Vtable の順序でメソッド  
 次の表は **IDebugCustomAttributeQuery の**  インターフェイスのメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|カスタム属性を名前であるかどうかを判定します。|  
|[GetCustomAttributeByName](../Topic/IDebugCustomAttributeQuery2::GetCustomAttributeByName.md)|特定のカスタム属性の属性情報を取得します。|  
  
 **IDebugCustomAttributeQuery の**  メソッドに加えて`IDebugCustomAttributeQuery2` は次のメソッドを実行します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|このフィールドに割り当てられているすべてのカスタム属性の列挙子を取得します。|  
  
## 解説  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) のメソッドはこのフィールドに対して定義されているすべてのカスタム属性の列挙子を返すことができます。  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [シンボルのプロバイダー インターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)