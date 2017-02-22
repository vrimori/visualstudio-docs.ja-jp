---
title: "IDebugProgram2 | Microsoft Docs"
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
  - "IDebugProgram2"
helpviewer_keywords: 
  - "IDebugProgram2 インターフェイス"
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはプロセスで実行中のプログラムを表します。  
  
## 構文  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジン \(DE\) とカスタム ポートの業者はプロセスのプログラムを表すためこのインターフェイスを実装します。  デバッグ セッションのマネージャーは \(SDM\)[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) に情報を提供するにはこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) のイベントは新しいプログラムのこのインターフェイスを返します。  このインターフェイスは複数のインターフェイスの多くのメソッドのパラメーターとして使用されます。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugProgram2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|このプログラムで実行しているスレッドを列挙します。|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|プログラムの名前を取得します。|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|このプログラムを実行しているプロセスを取得します。|  
|[終了](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|このプログラムを終了します。|  
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|これにアタッチしたりできます。|  
|[CanDetach](../Topic/IDebugProgram2::CanDetach.md)|デバッグ エンジンはプログラム \(DE\) からデタッチできるかどうかを判断します。|  
|[Detach](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|このプログラムからデバッガーをデタッチします。|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|このプログラムのグローバル一意識別子を取得します。|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|プログラムのプロパティを取得します。|  
|[実行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|停止状態からこのプログラムを実行する Continues。  の実行前の状態ではオフにします。|  
|[続行](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|停止状態からこのプログラムを実行する Continues。  の実行前の状態で保持されます。|  
|[ステップ](../../../extensibility/debugger/reference/idebugprogram2-step.md)|手順を実行します。|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|このプログラムの実行を停止し要求はスレッドの 1 つがコードを実行します。|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|このプログラムを実行するデバッグ エンジン \(DE\) の名前と ID を取得します。|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|ソース ファイル内の指定した位置のコード コンテキストを列挙します。|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|このプログラムのメモリのバイト数を取得します。|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|このプログラムのこの部分はプログラムの逆アセンブリ ストリームを取得します。|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|このプログラムを読み込む列挙しモジュールを実装しています。|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|編集を行います \(このプログラムの ENC\) を更新します。<br /><br /> カスタム デバッグ エンジンはこのメソッド \(`E_NOTIMPL` を常に返す必要があります\) を実装していません。|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|このプログラムのコード パスを列挙します。|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|ダンプをファイルに書き込みます。|  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 解説  
 プログラムはプロセスは一つ以上のプログラムから成るが特定のランタイム アーキテクチャで実行中のスレッドのコンテナーです。  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../Topic/IDebugThread2::GetProgram.md)   
 [次へ](../Topic/IEnumDebugPrograms2::Next.md)   
 [イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)