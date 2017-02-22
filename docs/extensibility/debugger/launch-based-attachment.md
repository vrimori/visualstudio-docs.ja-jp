---
title: "添付ファイルの起動に基づく | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "デバッグ エンジンを起動します。"
  - "デバッグ エンジンは、プログラムへのアタッチ"
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# 添付ファイルの起動に基づく
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プログラムの起動ベースの添付ファイルは自動的に実行されます。  プロセスホスティング SDM によってプログラムが起動するとき開始ベースの添付ファイルは手動添付ファイルのメソッドと同様のパスが表示されます。  ついては[プログラムへのアタッチ](../../extensibility/debugger/attaching-to-the-program.md) を参照してください。  
  
## アタッチの手順  
 主な違いは以下のとおり  **アタッチ**  の呼び出しの後のイベントのシーケンスです :  
  
1.  SDM への **IDebugEngineCreateEvent2** のイベント オブジェクトを送信します。  詳細については[イベントの送信](../../extensibility/debugger/sending-events.md) を参照してください。  
  
2.  **アタッチ**  のメソッドに渡される **IDebugProgram2** のインターフェイス `IDebugProgram2::GetProgramId` のメソッドを呼び出します。  
  
3.  DE にプログラムを表すために **IDebugProgram2** のローカル オブジェクト SDM が作成されたことを通知する **IDebugProgramCreateEvent2** のイベント オブジェクトを送信します。  
  
4.  新しいスレッドを起動したプロセス用に作成された SDM ことを通知する [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) のイベント オブジェクトを送信します。  
  
## 参照  
 [必要なイベントを送信します。](../../extensibility/debugger/sending-the-required-events.md)   
 [デバッグするプログラムを有効にします。](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)