---
title: アクティブ スクリプト デバッガー インターフェイス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Active Script Debugger interfaces
- activdbg.h
ms.assetid: bf4750b1-4e58-442b-ab56-254e640de61d
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4a3d17a8ff43bb3bd18641c2298f5436f40d925
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24642672"
---
# <a name="active-script-debugger-interfaces"></a>アクティブ スクリプト デバッガー インターフェイス
activdbg.h および activdbg100.h ヘッダー ファイルは、このセクションに記載されているインターフェイス、列挙型、および構造体を提供します。 これらはデバッグ スクリプト用です。  
  
> [!NOTE]
>  `IJSDebug*` インターフェイスおよび `IEnumJsStackFrames` インターフェイスは、スクリプトを含むネイティブ コードのデバッグ用に最初に Internet Explorer 11 でリリースされました。 これらのインターフェイスのヘッダー ファイルは jscript9diag.h です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 次のインターフェイスによって、言語およびホストに依存しないデバッグが可能になります。  
  
-   [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)  
  
-   [IActiveScriptDebug インターフェイス](../../winscript/reference/iactivescriptdebug-interface.md)  
  
-   [IActiveScriptErrorDebug インターフェイス](../../winscript/reference/iactivescripterrordebug-interface.md)  
  
-   [IActiveScriptErrorDebug110 インターフェイス](../../winscript/reference/iactivescripterrordebug110-interface.md)  
  
-   [IActiveScriptSiteDebug インターフェイス](../../winscript/reference/iactivescriptsitedebug-interface.md)  
  
-   [IActiveScriptSiteDebug32 インターフェイス](../../winscript/reference/iactivescriptsitedebug32-interface.md)  
  
-   [IActiveScriptSiteDebugEx インターフェイス](../../winscript/reference/iactivescriptsitedebugex-interface.md)  
  
-   [IActiveScriptWinRTErrorDebug インターフェイス](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)  
  
-   [IApplicationDebugger インターフェイス](../../winscript/reference/iapplicationdebugger-interface.md)  
  
-   [IApplicationDebuggerUI インターフェイス](../../winscript/reference/iapplicationdebuggerui-interface.md)  
  
-   [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)  
  
-   [IDebugApplication110 インターフェイス](../../winscript/reference/idebugapplication110-interface.md)  
  
-   [IDebugApplicationNode インターフェイス](../../winscript/reference/idebugapplicationnode-interface.md)  
  
-   [IDebugApplicationNode100 インターフェイス](../../winscript/reference/idebugapplicationnode100-interface.md)  
  
-   [IDebugApplicationNodeEvents インターフェイス](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
  
-   [IDebugApplicationThread インターフェイス](../../winscript/reference/idebugapplicationthread-interface.md)  
  
-   [IDebugApplicationThread110 インターフェイス](../../winscript/reference/idebugapplicationthread110-interface.md)  
  
-   [IDebugApplicationThreadEvents110 インターフェイス](../../winscript/reference/idebugapplicationthreadevents110-interface.md)  
  
-   [IDebugAsyncOperation インターフェイス](../../winscript/reference/idebugasyncoperation-interface.md)  
  
-   [IDebugAsyncOperationCallBack インターフェイス](../../winscript/reference/idebugasyncoperationcallback-interface.md)  
  
-   [IDebugCodeContext インターフェイス](../../winscript/reference/idebugcodecontext-interface.md)  
  
-   [IDebugCookie インターフェイス](../../winscript/reference/idebugcookie-interface.md)  
  
-   [IDebugDocument インターフェイス](../../winscript/reference/idebugdocument-interface.md)  
  
-   [IDebugDocumentContext インターフェイス](../../winscript/reference/idebugdocumentcontext-interface.md)  
  
-   [IDebugDocumentHelper インターフェイス](../../winscript/reference/idebugdocumenthelper-interface.md)  
  
-   [IDebugDocumentHost インターフェイス](../../winscript/reference/idebugdocumenthost-interface.md)  
  
-   [IDebugDocumentInfo インターフェイス](../../winscript/reference/idebugdocumentinfo-interface.md)  
  
-   [IDebugDocumentProvider インターフェイス](../../winscript/reference/idebugdocumentprovider-interface.md)  
  
-   [IDebugDocumentText インターフェイス](../../winscript/reference/idebugdocumenttext-interface.md)  
  
-   [IDebugDocumentTextAuthor インターフェイス](../../winscript/reference/idebugdocumenttextauthor-interface.md)  
  
-   [IDebugDocumentTextEvents インターフェイス](../../winscript/reference/idebugdocumenttextevents-interface.md)  
  
-   [IDebugDocumentTextExternalAuthor インターフェイス](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)  
  
-   [IDebugExpression インターフェイス](../../winscript/reference/idebugexpression-interface.md)  
  
-   [IDebugExpressionCallBack インターフェイス](../../winscript/reference/idebugexpressioncallback-interface.md)  
  
-   [IDebugExpressionContext インターフェイス](../../winscript/reference/idebugexpressioncontext-interface.md)  
  
-   [IDebugFormatter インターフェイス](../../winscript/reference/idebugformatter-interface.md)  
  
-   [IDebugHelper インターフェイス](../../winscript/reference/idebughelper-interface.md)  
  
-   [IDebugSessionProvider インターフェイス](../../winscript/reference/idebugsessionprovider-interface.md)  
  
-   [IDebugSessionProviderEx インターフェイス](../../winscript/reference/idebugsessionproviderex-interface.md)  
  
-   [IDebugStackFrame インターフェイス](../../winscript/reference/idebugstackframe-interface.md)  
  
-   [IDebugStackFrameSniffer インターフェイス](../../winscript/reference/idebugstackframesniffer-interface.md)  
  
-   [IDebugStackFrameSnifferEx インターフェイス](../../winscript/reference/idebugstackframesnifferex-interface.md)  
  
-   [IDebugSyncOperation インターフェイス](../../winscript/reference/idebugsyncoperation-interface.md)  
  
-   [IDebugThreadCall インターフェイス](../../winscript/reference/idebugthreadcall-interface.md)  
  
-   [IEnumDebugApplicationNodes インターフェイス](../../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  
-   [IEnumDebugCodeContexts インターフェイス](../../winscript/reference/ienumdebugcodecontexts-interface.md)  
  
-   [IEnumDebugExpressionContexts インターフェイス](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  
-   [IEnumDebugStackFrames インターフェイス](../../winscript/reference/ienumdebugstackframes-interface.md)  
  
-   [IEnumJsStackFrames インターフェイス](../../winscript/reference/ienumjsstackframes-interface.md)  
  
-   [IEnumRemoteDebugApplications インターフェイス](../../winscript/reference/ienumremotedebugapplications-interface.md)  
  
-   [IEnumRemoteDebugApplicationThreads インターフェイス](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  
-   [IJsDebug インターフェイス](../../winscript/reference/ijsdebug-interface.md)  
  
-   [IJsDebugBreakPoint インターフェイス](../../winscript/reference/ijsdebugbreakpoint-interface.md)  
  
-   [IJsDebugDataTarget インターフェイス](../../winscript/reference/ijsdebugdatatarget-interface.md)  
  
-   [IJsDebugFrame インターフェイス](../../winscript/reference/ijsdebugframe-interface.md)  
  
-   [IJsDebugProcess インターフェイス](../../winscript/reference/ijsdebugprocess-interface.md)  
  
-   [IJsDebugProperty インターフェイス](../../winscript/reference/ijsdebugproperty-interface.md)  
  
-   [IJsDebugStackWalker インターフェイス](../../winscript/reference/ijsdebugstackwalker-interface.md)  
  
-   [IJsEnumDebugProperty インターフェイス](../../winscript/reference/ijsenumdebugproperty-interface.md)  
  
-   [IMachineDebugManager インターフェイス](../../winscript/reference/imachinedebugmanager-interface.md)  
  
-   [IMachineDebugManagerCookie インターフェイス](../../winscript/reference/imachinedebugmanagercookie-interface.md)  
  
-   [IMachineDebugManagerEvents インターフェイス](../../winscript/reference/imachinedebugmanagerevents-interface.md)  
  
-   [IProcessDebugManager インターフェイス](../../winscript/reference/iprocessdebugmanager-interface.md)  
  
-   [IProvideExpressionContexts インターフェイス](../../winscript/reference/iprovideexpressioncontexts-interface.md)  
  
-   [IRemoteDebugApplication インターフェイス](../../winscript/reference/iremotedebugapplication-interface.md)  
  
-   [IRemoteDebugApplication110 インターフェイス](../../winscript/reference/iremotedebugapplication110-interface.md)  
  
-   [IRemoteDebugApplicationEx インターフェイス](../../winscript/reference/iremotedebugapplicationex-interface.md)  
  
-   [IRemoteDebugApplicationEvents インターフェイス](../../winscript/reference/iremotedebugapplicationevents-interface.md)  
  
-   [IRemoteDebugApplicationThread インターフェイス](../../winscript/reference/iremotedebugapplicationthread-interface.md)  
  
-   [IRemoteDebugApplicationThreadEx インターフェイス](../../winscript/reference/iremotedebugapplicationthreadex-interface.md)  
  
-   [ISetNextStatement インターフェイス](../../winscript/reference/isetnextstatement-interface.md)  
  
-   [ISimpleConnectionPoint インターフェイス](../../winscript/reference/isimpleconnectionpoint-interface.md)  
  
-   [IWebAppDiagnosticsSetup インターフェイス](../../winscript/reference/iwebappdiagnosticssetup-interface.md)  
  
-   [IWebAppDiagnosticsObjectInitialization インターフェイス](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)  
  
 次のセクションでは、デバッグで使用される定数、列挙型、および構造体の一覧を示します。  
  
-   [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプトのデバッグの概要](../../winscript/active-script-debugging-overview.md)