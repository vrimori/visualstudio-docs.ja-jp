---
title: "IRemoteDebugApplication インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication インターフェイス"
ms.assetid: 96bf2a3f-049f-46ba-86ad-57fc184343a2
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IRemoteDebugApplication インターフェイス
実行中のアプリケーションを表します。  これは、オペレーティング システム プロセスに対応する必要はありません。  通常、デバッグ対象のアプリケーションを対象とします。  プロセス デバッグ マネージャーは、通常、アプリケーション オブジェクトを実装します。  
  
 `IUnknown` から継承するメソッドに加え、`IRemoteDebugApplication` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)|ブレークポイントに存在するアプリケーションを続行します。|  
|[IRemoteDebugApplication::CauseBreak](../../winscript/reference/iremotedebugapplication-causebreak.md)|デバッガーにできるだけ早くアプリケーションを中断します。|  
|[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)|このアプリケーションにデバッガーを接続します。|  
|[IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)|アプリケーションから現在のデバッガーをドロップします。|  
|[IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)|接続されたアプリケーションに現在のデバッガーを返します。|  
|[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)|デバッガーでなく、機構、アプリケーション プロセスのオブジェクトを作成するアプリケーションの実行中のプロセスを提供します。|  
|[IRemoteDebugApplication::QueryAlive](../../winscript/reference/iremotedebugapplication-queryalive.md)|アプリケーションが依存するかどうかを示します。|  
|[IRemoteDebugApplication::EnumThreads](../../winscript/reference/iremotedebugapplication-enumthreads.md)|アプリケーションに関連付けられているためにわかっているすべてのスレッドを列挙します。|  
|[IRemoteDebugApplication::GetName](../../winscript/reference/iremotedebugapplication-getname.md)|このアプリケーション ノードの名前を返します。|  
|[IRemoteDebugApplication::GetRootNode](../../winscript/reference/iremotedebugapplication-getrootnode.md)|アプリケーションに関連付けられているすべてのノードが追加されたアプリケーションのノードを返します。|  
|[IRemoteDebugApplication::EnumGlobalExpressionContexts](../../winscript/reference/iremotedebugapplication-enumglobalexpressioncontexts.md)|このアプリケーションで実行されるすべての言語に対するグローバル コンテキスト式を列挙します。|