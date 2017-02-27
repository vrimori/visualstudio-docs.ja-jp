---
title: "IDebugMemoryContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2"
helpviewer_keywords: 
  - "IDebugMemoryContext2 インターフェイス"
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugMemoryContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはデバッグするプログラムを実行するコンピューターのアドレス空間の位置を表します。  
  
## 構文  
  
```  
IDebugMemoryContext2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンはメモリ \(DE\) 内のアドレスを表すためこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) または [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) の呼び出しはこのインターフェイスを返します。  また次の [追加](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) と [減算](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) の新しいコピーを呼び出すと適切な算術演算のインターフェイスが使用されました。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugMemoryContext2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|このコンテキストのユーザー表示できる名前を取得します。|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|このコンテキストを記述する情報を取得します。|  
|[追加](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|現在のコンテキストでのアドレスに指定された値を新しいコンテキストを作成するようにします。|  
|[減算](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|現在のコンテキストでのアドレスから指定された値を新しいコンテキストを作成するには減算します。|  
|[比較](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|使用方法の 2 つがのコンテキストを比較するフラグを比較します。|  
  
## 解説  
 評価される式を含む `IDebugMemoryContext2` のインターフェイスを取得 ENT0ENT Visual Studio の \[ウィンドウ\] の呼び出し [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) はメモリ アドレスに使用します。  このコンテキストは [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) と [WriteAt](../Topic/IDebugMemoryBytes2::WriteAt.md) の読み取りまたは書き込みを行うためにアドレスを指定するように渡されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)   
 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)   
 [WriteAt](../Topic/IDebugMemoryBytes2::WriteAt.md)