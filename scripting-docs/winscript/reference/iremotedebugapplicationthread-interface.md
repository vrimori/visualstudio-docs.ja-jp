---
title: "IRemoteDebugApplicationThread インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread インターフェイス"
ms.assetid: 062bb997-7b9e-4945-bfbe-d5b92d5cb707
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IRemoteDebugApplicationThread インターフェイス
特定のアプリケーション内の実行中のスレッドを表します。  
  
 `IUnknown` から継承するメソッドに加え、`IRemoteDebugApplicationThread` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IRemoteDebugApplicationThread::GetSystemThreadId](../../winscript/reference/iremotedebugapplicationthread-getsystemthreadid.md)|スレッドに関連付けられた動作 system–dependent の識別子を返します。|  
|[IRemoteDebugApplicationThread::GetApplication](../../winscript/reference/iremotedebugapplicationthread-getapplication.md)|このスレッドに関連付けられたアプリケーション オブジェクトを返します。|  
|[IRemoteDebugApplicationThread::EnumStackFrames](../../winscript/reference/iremotedebugapplicationthread-enumstackframes.md)|このスレッドに関連付けられているスタック フレームの列挙子を返します。|  
|[IRemoteDebugApplicationThread::GetDescription](../../winscript/reference/iremotedebugapplicationthread-getdescription.md)|このスレッドの説明と状態を取得します。|  
|[IRemoteDebugApplicationThread::SetNextStatement](../../winscript/reference/iremotedebugapplicationthread-setnextstatement.md)|特定のコード コンテキストに、特定のフレームのコンテキストで実行を継続できるだけ近い累乗。|  
|[IRemoteDebugApplicationThread::GetState](../../winscript/reference/iremotedebugapplicationthread-getstate.md)|このスレッドの状態を取得します。|  
|[IRemoteDebugApplicationThread::Suspend](../../winscript/reference/iremotedebugapplicationthread-suspend.md)|スレッドを中断します。|  
|[IRemoteDebugApplicationThread::Resume](../../winscript/reference/iremotedebugapplicationthread-resume.md)|スレッドを再開します。|  
|[IRemoteDebugApplicationThread::GetSuspendCount](../../winscript/reference/iremotedebugapplicationthread-getsuspendcount.md)|スレッドの中断カウントを返します。|