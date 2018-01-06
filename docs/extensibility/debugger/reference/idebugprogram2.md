---
title: "IDebugProgram2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2
helpviewer_keywords: IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7f02d099fe680006966219bb626e17bc7a7114b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2"></a>IDebugProgram2
このインターフェイスは、プロセスで実行されているプログラムを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) とそのカスタム ポート業者は、プロセスでプログラムを表すためには、このインターフェイスを実装します。 セッションのデバッグ マネージャー (SDM) も情報を提供するには、このインターフェイスを実装[アタッチ](../../../extensibility/debugger/reference/idebugprogram2-attach.md)です。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)イベントが新しいプログラムのこのインターフェイスを返します。 このインターフェイスは、複数のインターフェイスの多くのメソッドのパラメーターとしても使用されます。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugProgram2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|このプログラムで実行されているスレッドを列挙します。|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|プログラムの名前を取得します。|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|このプログラムがで実行されているプロセスを取得します。|  
|[終了](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|このプログラムを終了します。|  
|[添付](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|このプログラムにアタッチします。|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|デバッグ エンジン (DE) が、プログラムから切り離すことができるかどうかを判断します。|  
|[デタッチ](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|このプログラムからデバッガーをデタッチします。|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|このプログラムのグローバルに一意の識別子を取得します。|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|プログラムのプロパティを取得します。|  
|[実行します。](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|停止状態からこのプログラムの実行が続行されます。 以前の実行状態がクリアされます。|  
|[Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|停止状態からこのプログラムの実行が続行されます。 以前の実行状態が維持されます。|  
|[Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)|ステップを実行します。|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|このプログラムが次の実行を停止する要求は、そのスレッドの実行のコードのいずれかの時間です。|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|このプログラムを実行するデバッグ エンジン (DE) の識別子と名前を取得します。|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|ソース ファイル内の指定位置にコードのコンテキストを列挙します。|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|このプログラムのメモリのバイト数を取得します。|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|このプログラムまたはこのプログラムの一部の逆アセンブリ ストリームを取得します。|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|このプログラムが読み込まれが実行しているモジュールを列挙します。|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|このプログラムの編集と続行 (ENC) 更新プログラムを取得します。<br /><br /> カスタム デバッグ エンジンは、このメソッドを実装しない (常に返すか`E_NOTIMPL`)。|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|このプログラムのコード パスを列挙します。|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|ダンプ ファイルを書き込みます。|  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>コメント  
 プログラムは、プロセスで構成される 1 つまたは複数のプログラムの中に、特定のランタイムのアーキテクチャで実行されているスレッド コンテナーです。  
  
## <a name="see-also"></a>参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [次に](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)