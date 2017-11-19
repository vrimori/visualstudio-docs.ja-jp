---
title: "IDebugPortEx2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortEx2
helpviewer_keywords: IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 06eab3133669381d13416c0990370ad01378222c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportex2"></a>IDebugPortEx2
このインターフェイスは、プログラムとポートで実行されているプロセス マネージャー (SDM) コントロールをデバッグ セッションを使用します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugPortEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 カスタム ポート業者を実装する同一のオブジェクトにこのインターフェイスを実装する[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)です。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 SDM 呼び出し[QueryInterface](/cpp/atl/queryinterface)上、`IDebugPort2`インターフェイスをこのインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugPortEx2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|実行可能ファイルを起動します。|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|プロセスの実行を再開します。|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|プロセスを終了できるかどうかを判断します。|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|プロセスを終了します。|  
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|ポート自体のプロセス ID を取得します。|  
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|プログラムのノードに関連付けられているプログラムを取得します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスは、通常、SDM とカスタム ポート仕入先の間でプライベートです。  
  
 必要な場合、デバッグ エンジン (DE) を検索できるこのインターフェイス、 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)に渡されたインターフェイス[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)を使用して[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)プログラムを起動します。 これが要件ではありません、ただしであり、DE ことができます要求プログラムを起動するために必要なものです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)