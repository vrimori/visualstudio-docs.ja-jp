---
title: "IDebugGenericFieldDefinition | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugGenericFieldDefinition インターフェイス"
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugGenericFieldDefinition
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

マネージ コードのジェネリック型のフィールドの定義を表します。  
  
## 構文  
  
```  
IDebugGenericFieldDefinition : IUnknown  
```  
  
## メソッド  
 このインターフェイスは以下のメソッドを実行します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|型引数の配列を持つフィールドのインスタンスを構築します。|  
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|パラメーターの値は型パラメーターを取得します。|  
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|一般的なフィールドに関連付けられた型パラメーターの数を取得します。|  
  
## 必要条件  
 ヘッダー : Sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll