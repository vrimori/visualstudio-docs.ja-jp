---
title: "IEnumDebugPrograms2 | Microsoft Docs"
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
  - "IEnumDebugPrograms2"
helpviewer_keywords: 
  - "IEnumDebugPrograms2"
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugPrograms2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスは現在のデバッグ セッションで実行するプログラムを列挙します。  
  
## 構文  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンはde\-DE \(DE\) でデバッグするプログラムの一覧を表示するにはこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 Visual Studio はこのインターフェイスを取得するに [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) を呼び出します。  [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) はVisual Studio では使用されません。  
  
## Vtable の順序でメソッド  
 次の表は `IEnumDebugPrograms2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[次へ](../Topic/IEnumDebugPrograms2::Next.md)|列挙体シーケンス内の指定した数のプログラムを取得します。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|列挙体シーケンスのプログラムから指定した数の要素をスキップします。|  
|[リセット](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|列挙体シーケンスを先頭にリセットします。|  
|[複製](../Topic/IEnumDebugPrograms2::Clone.md)|現在の列挙子と同じ列挙状態を含む列挙子を作成します。|  
|[GetCount](../Topic/IEnumDebugPrograms2::GetCount.md)|列挙子のプログラムの数を取得します。|  
  
## 解説  
 Visual Studio はこのインターフェイスを使用して :  
  
-   \[出力\] ウィンドウ ENT0ENT 設定します \([EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) を呼び出すとプログラムの [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) を呼び出すことにより\)。  
  
-   \[入力\] ENT0ENT リストを生成します \(`IDebugProcess2::EnumPrograms` を呼び出すと [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) のインターフェイスを取得するに [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) の各インターフェイスに [QueryInterface](/visual-cpp/atl/queryinterface) を呼び出すことにより\)。  
  
-   プロセスの各プログラムをデバッグする DEs のリストを生成します \([GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) を使用します。  
  
-   編集を適用し各プログラム \(ENC\) 更新を続行する \(IDebugProcess2 を呼び出して :: EnumPrograms し呼び出し元の [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)\)。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)