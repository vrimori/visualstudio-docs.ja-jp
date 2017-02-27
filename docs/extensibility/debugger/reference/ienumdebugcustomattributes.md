---
title: "IEnumDebugCustomAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumCustomAttributes"
helpviewer_keywords: 
  - "IEnumDebugCustomAttributes インターフェイス"
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IEnumDebugCustomAttributes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

カスタム属性を列挙します。  
  
## 構文  
  
```  
IEnumCustomAttributes : IUnknown  
```  
  
## 実装についてのメモ  
 シンボルのプロバイダーはカスタム属性をサポートするにはこのインターフェイスを実装します。[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) のインターフェイスを行います。  
  
## 呼び出し元のメモ  
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) はこのインターフェイスを返します。  
  
## Vtable の順序でメソッド  
 次の表は `IEnumDebugCustomAttributes` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|列挙体シーケンス内の指定した数のカスタム属性を取得します。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|列挙体シーケンス内のカスタム属性の指定した数の要素をスキップします。|  
|[リセット](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|列挙体シーケンスを先頭にリセットします。|  
|[複製](../Topic/IEnumDebugCustomAttributes::Clone.md)|現在の列挙子と同じ列挙状態を含む列挙子を作成します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|列挙子のカスタム属性の数を取得します。|  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [シンボルのプロバイダー インターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)