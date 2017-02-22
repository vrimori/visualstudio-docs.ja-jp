---
title: "IDebugReference2 | Microsoft Docs"
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
  - "IDebugReference2"
helpviewer_keywords: 
  - "IDebugReference2 インターフェイス"
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugReference2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスにはスタック フレームのプロパティやそのほかのプロパティへの参照を表します。  
  
> [!NOTE]
>  `IDebugReference2` は今後使用するために予約されてメソッドはすべて `E_NOTIMPL` を返す必要があります。  
  
## 構文  
  
```  
IDebugReference2 : IUnknown  
```  
  
## 実装についてのメモ  
 DE implements 値の特定の型への参照を表します。このインターフェイス  たとえば値が式の評価メモリの表示に使用されるメモリのコンテキストまたは登録の一覧と値の結果として数値を使用できます。  
  
## 呼び出し元のメモ  
 このインターフェイスを取得します [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)。  [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) と [GetDerivedMostReference](../Topic/IDebugReference2::GetDerivedMostReference.md) はこのインターフェイスを返します。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugReference2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|この参照を記述する [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) の構造体を取得します。|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|文字列からこの参照の値を設定します。|  
|[SetValueAsReference](../Topic/IDebugReference2::SetValueAsReference.md)|別の参照からこの参照の値を設定します。|  
|[EnumChildren](../Topic/IDebugReference2::EnumChildren.md)|この参照の子を列挙します。|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|この参照の親を取得します。|  
|[GetDerivedMostReference](../Topic/IDebugReference2::GetDerivedMostReference.md)|この参照は最派生の参照を取得します。|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|をこの参照によって参照されるメモリのバイト取得します。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|この参照のメモリのコンテキストを取得します。|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|サイズがこの参照のサイズ \(バイト単位\) を取得します。|  
|[SetReferenceType](../Topic/IDebugReference2::SetReferenceType.md)|この参照型を設定します。|  
|[比較](../../../extensibility/debugger/reference/idebugreference2-compare.md)|別のこの参照を比較します。|  
  
## 解説  
  
> [!NOTE]
>  「プロパティ」をこのように使用するとその `IDebugReference2` がこのようなエンティティをできますがクラスのメンバー変数混同しないようにしてください。  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) は `IDebugReference2` はプロパティへの参照を表しますがおよびプロパティをデバッグするプログラムのオブジェクトへの参照表します。  
  
 プロパティで参照との主な相違点は参照がないインスタンスを示していますがプロパティがオブジェクトの名前付きインスタンスを参照していることです。  たとえばプロパティは `"a.b"` とプログラムのヒープのオブジェクトを示している可能性があります。  別のプロパティが `"c.d"` と同じオブジェクトを示している可能性があります。  このプロパティを表示する方法は`"a.b"` が必要です。または `"c.d"` がスコープ内にあります。  このオブジェクトへの参照がない。; オブジェクトはそのオブジェクトのメモリが有効な場合に参照できます。  
  
 名前型およびアドレスでの `IDebugProperty2` のインターフェイスは値と考えることができます。  `IDebugReference2` は型としてアドレスと考えることができます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)