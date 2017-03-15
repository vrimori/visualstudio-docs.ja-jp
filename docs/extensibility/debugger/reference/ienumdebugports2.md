---
title: "IEnumDebugPorts2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPorts2"
helpviewer_keywords: 
  - "IEnumDebugPorts2"
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IEnumDebugPorts2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはコンピューターまたはポートの仕入先ポートを列挙します。  
  
## 構文  
  
```  
IEnumDebugPorts2 : IUnknown  
```  
  
## 実装についてのメモ  
 カスタム ポートのサプライヤーがサプライヤーが作成されるポートの一覧を表すにはこのインターフェイスを実装します。  Visual Studio はポートのサプライヤーを確保このインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 ポートの一覧を表すこのインターフェイスを取得します [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) はポートのサプライヤーして作成します。  ディスクに保存されたポートの一覧を表すこのインターフェイスを取得するに [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) を呼び出します。  
  
## Vtable の順序でメソッド  
 次の表は `IEnumDebugPorts2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|列挙体シーケンス内の指定した数のポートを取得します。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|列挙体シーケンス内の指定した数のポートをスキップします。|  
|[リセット](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|列挙体シーケンスを先頭にリセットします。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|現在の列挙子と同じ列挙状態を含む列挙子を作成します。|  
|[GetCount](../Topic/IEnumDebugPorts2::GetCount.md)|列挙子のポートの番号を取得します。|  
  
## 解説  
 Visual Studio がプロセスにアタッチするために使用するポートの一覧を取得するにはこのインターフェイスを使用します。  
  
 デバッグ エンジンは通常このインターフェイスを使用しません。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)