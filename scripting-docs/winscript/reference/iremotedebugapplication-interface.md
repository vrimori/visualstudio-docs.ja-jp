---
title: IRemoteDebugApplication インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication interface
ms.assetid: 96bf2a3f-049f-46ba-86ad-57fc184343a2
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02ddf409bf25cb86fc742cdc004e2f1b664d22e3
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348764"
---
# <a name="iremotedebugapplication-interface"></a>IRemoteDebugApplication インターフェイス
実行中のアプリケーションを表します。 オペレーティング システムのプロセスに対応する必要はありません。 通常、デバッガーはデバッグ用のアプリケーションを対象とします。 プロセス デバッグ マネージャーは、通常、アプリケーション オブジェクトを実装します。  
  
 継承されたメソッドだけでなく`IUnknown`、`IRemoteDebugApplication`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)|ブレークポイントになっているアプリケーションを継続します。|  
|[IRemoteDebugApplication::CauseBreak](../../winscript/reference/iremotedebugapplication-causebreak.md)|により、アプリケーションは、できるだけ早い機会にデバッガーを中断します。|  
|[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)|このアプリケーションにデバッガーを接続します。|  
|[IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)|アプリケーションから現在のデバッガーを切断します。|  
|[IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)|アプリケーションに接続されている現在のデバッガーを返します。|  
|[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)|IDE、実行中のプロセス外アプリケーション プロセスでオブジェクトを作成する、アプリケーションにデバッガーのメカニズムを提供します。|  
|[IRemoteDebugApplication::QueryAlive](../../winscript/reference/iremotedebugapplication-queryalive.md)|アプリケーションが応答性の高いかどうかを示します。|  
|[IRemoteDebugApplication::EnumThreads](../../winscript/reference/iremotedebugapplication-enumthreads.md)|既知のアプリケーションに関連するすべてのスレッドを列挙します。|  
|[IRemoteDebugApplication::GetName](../../winscript/reference/iremotedebugapplication-getname.md)|このアプリケーションのノードの名前を返します。|  
|[IRemoteDebugApplication::GetRootNode](../../winscript/reference/iremotedebugapplication-getrootnode.md)|アプリケーションに関連付けられているすべてのノードを追加するアプリケーションのノードを返します。|  
|[IRemoteDebugApplication::EnumGlobalExpressionContexts](../../winscript/reference/iremotedebugapplication-enumglobalexpressioncontexts.md)|このアプリケーションで実行されているすべての言語用のグローバル式のコンテキストを列挙します。|