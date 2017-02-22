---
title: "IEnumDebugReferenceInfo2 | Microsoft Docs"
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
  - "IEnumDebugReferenceInfo2"
helpviewer_keywords: 
  - "IEnumDebugReferenceInfo2"
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugReferenceInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスは [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) の構造を列挙します。  
  
## 構文  
  
```  
IEnumDebugReferenceInfo2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンはメモリ \(DE\) 内のオブジェクトへの参照のサポートの一部としてこのインターフェイスを実装します。  このインターフェイスは参照がサポートされている場合のみ実行する必要があります。  
  
## 呼び出し元のメモ  
 Visual Studio はこのインターフェイスを取得するに [EnumChildren](../Topic/IDebugReference2::EnumChildren.md) を呼び出します。  
  
## Vtable の順序でメソッド  
 次の表は `IEnumDebugReferenceInfo2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|列挙体シーケンス内の指定 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) の構造体の数を取得します。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|列挙体シーケンス内の [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 構造の指定した数の要素をスキップします。|  
|[リセット](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|列挙体シーケンスを先頭にリセットします。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|現在の列挙子と同じ列挙状態を含む列挙子を作成します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|列挙子の [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) の構造体の数を取得します。|  
  
## 解説  
 参照はプロパティの名前型およびアドレスであり主に型とアドレスです。  参照は参照されるオブジェクトがメモリに存在する限り保持されます。  詳細については、「[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)」を参照してください。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [EnumChildren](../Topic/IDebugReference2::EnumChildren.md)