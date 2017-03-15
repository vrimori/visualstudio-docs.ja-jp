---
title: "ポートへの通知 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "通知のポート"
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# ポートへの通知
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プログラムが起動したらポートは次のとおり知らせられなければがあります :  
  
1.  ポートは新しいプログラムのノードを受け取るとデバッグ セッションにプログラムの作成イベントを返します。  イベントとはプログラムを表すインターフェイスを行います。  
  
2.  デバッグ セッションをアタッチできるデバッグ エンジン \(DE\) ID のプログラムを呼び出します。  
  
3.  デバッグ セッションは機能しますがプログラムに使用可能な DEs の一覧にあるかどうかを確認します。  デバッグ セッションは最初にデバッグのパッケージ渡されたソリューションのアクティブなプログラムの設定をこのリストを取得します。  
  
     DE が有効なリストです。しますがプログラムにアタッチされません。  
  
 ポートは最初に新しいプログラムのノードを受け取るとプログラムによってプログラムを表すために [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) のインターフェイスを作成します。  
  
> [!NOTE]
>  これはデバッグ エンジン \(DE\) により後に作成された `IDebugProgram2` インターフェイスと混同しないようにしてください。  
  
 ポートはCOM `IConnectionPoint` のインターフェイスによってデバッグ セッションのマネージャー \(SDM\) に [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) プログラムの作成イベントを返します。  
  
> [!NOTE]
>  これはde\-DE に後で送信 `IDebugProgramCreateEvent2` インターフェイスと混同しないようにしてください。  
  
 イベント インターフェイス自体とともにポートの [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)[IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) を送信しポートを表す [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) のインターフェイスを処理しそれぞれをお勧めします。  SDM でプログラムをデバッグできる DE の GUID を取得するに [IDebugProgram2:: GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) を呼び出します。  GUID は最初に [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) インターフェイスから派生しています。  
  
 SDM は機能しますが有効な DEs の一覧にあるかどうかを確認します。  SDM は最初にデバッグのパッケージ渡されたソリューションのアクティブなプログラムの設定をこのリストを取得します。  DE が有効なリストであるかまたはプログラムにアタッチされません。  
  
 一度に DE ID はSDM プログラムにアタッチする準備が整いました。呼ばれます。  
  
## 参照  
 [プログラムの起動](../../extensibility/debugger/launching-a-program.md)   
 [起動した後にアタッチします。](../../extensibility/debugger/attaching-after-a-launch.md)   
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)