---
title: "IDebugProgramHost2 | Microsoft Docs"
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
  - "IDebugProgramHost2"
helpviewer_keywords: 
  - "IDebugProgramHost2 インターフェイス"
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramHost2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはプログラムのホスト プロセス \(\) 情報を提供します。  
  
## 構文  
  
```  
IDebugProgramHost2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンは[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) インターフェイスとホスティングプロセスに関する情報を提供するために同じオブジェクトこのインターフェイスを実装します。  これは省略可能なインターフェイスです。  
  
## 呼び出し元のメモ  
 このインターフェイスを取得 `IDebugProgram2` のインターフェイスでは [QueryInterface](/visual-cpp/atl/queryinterface)。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugProgramHost2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|このプログラムのホスティングプロセスのタイトル表示名またはファイル名を取得します。|  
|[含ま](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|このプログラムのホスティングプロセスのプロセス識別子を取得します。|  
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|このプログラムのホスティングプロセスが実行されているコンピューターの名前を取得します。|  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)