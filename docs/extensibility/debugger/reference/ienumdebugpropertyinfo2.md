---
title: "IEnumDebugPropertyInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPropertyInfo2"
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo2"
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugPropertyInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスは [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) の構造を列挙します。  
  
## 構文  
  
```  
IEnumDebugPropertyInfo2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンは \(DE\)特定のプロパティの情報を表すためこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 特定のプロパティの子を表すこのインターフェイスを取得するに [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) を呼び出します。  特定のスタック フレームのプロパティを表すこのインターフェイスを取得します [EnumProperties](../Topic/IDebugStackFrame2::EnumProperties.md)。  
  
## Vtable の順序でメソッド  
 次の表は `IEnumDebugPropertyInfo2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|列挙体シーケンス内の指定 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) の構造体の数を取得します。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|列挙体シーケンス内の [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 構造の指定した数の要素をスキップします。|  
|[リセット](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|列挙体シーケンスを先頭にリセットします。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|現在の列挙子と同じ列挙状態を含む列挙子を作成します。|  
|[GetCount](../Topic/IEnumDebugPropertyInfo2::GetCount.md)|列挙子の [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) の構造体の数を取得します。|  
  
## 解説  
 通常プロパティは関連付けられたプロパティのオブジェクトまたはスタック フレームに適切なそのほかの情報を含む名前評価アドレス入力できる情報の階層です。  詳細については、「[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)」を参照してください。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../Topic/IDebugStackFrame2::EnumProperties.md)