---
title: IDebugPortEx2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f574d610058ffa77408a95b80c64a844074ed025
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53876459"
---
# <a name="idebugportex2"></a>IDebugPortEx2
このインターフェイスには、プログラムとポートで実行されているプロセス マネージャー (SDM) コントロールのデバッグ セッションことができます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugPortEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 カスタム ポートのサプライヤーを実装する同一のオブジェクトにこのインターフェイスを実装する[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 SDM コール[QueryInterface](/cpp/atl/queryinterface)上、`IDebugPort2`をこのインターフェイスを取得するインターフェイス。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugPortEx2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|実行可能ファイルを起動します。|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|プロセスの実行を再開します。|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|プロセスが終了するかどうかを判断します。|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|プロセスを終了します。|  
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|ポート自体のプロセス ID を取得します。|  
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|プログラム ノードに関連付けられているプログラムを取得します。|  
  
## <a name="remarks"></a>Remarks  
 このインターフェイスは、SDM とカスタム ポート サプライヤー間通常プライベートです。  
  
 デバッグ エンジン (DE) にこのインターフェイスの参照することが必要な場合、 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)に渡されたインターフェイス[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)して[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)プログラムを起動します。 これは要件ではありません、ただし、あり要求プログラムを起動するために必要な DE が行うことができます。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: portpriv.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)