---
title: "IDebugProgramNodeAttach2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNodeAttach2"
helpviewer_keywords: 
  - "IDebugProgramNodeAttach2 インターフェイス"
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 3
---
# IDebugProgramNodeAttach2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プログラムのノードに関連付けられているプログラムにアタッチしようを通知できます。  
  
## 構文  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## 実装についてのメモ  
 このインターフェイスはアタッチ操作の通知の受け取りアタッチ操作を取り消す機会を提供するために [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) のインターフェイスを実装する同じクラスに実装されます。  
  
## 呼び出し元のメモ  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) のオブジェクトの `QueryInterface` のメソッドを呼び出してこのインターフェイスを取得します。  [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) のメソッドは前のメソッドに [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) プログラムのノードにアタッチするプロセスを停止できるように呼び出す必要があります。  
  
## Vtable の順序でメソッド  
 このインターフェイスは以下のメソッドを実行します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|関連するプログラムまたは延期にアタッチしたり [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) のメソッドにアタッチするプロセス。|  
  
## 解説  
 このインターフェイスは [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) の使用されていないメソッドに推奨される方法です。  すべてのデバッグ エンジンは`CoCreateInstance` の関数と常に読み込まれます。つまりデバッグするプログラムのアドレス空間以外でインスタンス化されます。  
  
 `IDebugProgramNode2::Attach_V7` のメソッドの実装をデバッグするプログラムの `GUID` を設定する [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) のメソッドに実装する必要があります。  
  
 `IDebugProgramNode2::Attach_V7` のメソッドの実装が提供されるコールバック インターフェイスを使用すると機能が [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) のメソッドと `IDebugProgramNodeAttach2` のインターフェイスの実装に移動する必要があるため実装する必要はありません。  
  
## 必要条件  
 ヘッダー : Msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)