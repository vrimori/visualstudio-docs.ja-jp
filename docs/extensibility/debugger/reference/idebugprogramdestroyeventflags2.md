---
title: "IDebugProgramDestroyEventFlags2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProgramDestroyEventFlags2 インターフェイス"
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugProgramDestroyEventFlags2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

デバッグ セッションを終了時にデバッグ エンジンは [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] の UI  の既定の動作をオーバーライドできます。  
  
## 構文  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## 実装についてのメモ  
 このインターフェイスはデバッグ エンジンによって実装されます。  これはプロセスの有効期間にわたって複数のプログラムの作成と破棄する可能性のあるホストで役立ちます。  
  
## メソッド  
 次の表は `IDebugProgramDestroyEventFlags2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|プログラムの破棄フラグを取得します。|  
  
## 解説  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] の UI  の既定の動作ではすべてのプログラムはプログラムの破棄イベントを送信しデザイン モードに戻ることです。  このインターフェイスは動作の変更はデバッグ エンジンができます。  
  
## 必要条件  
 ヘッダー : Msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll