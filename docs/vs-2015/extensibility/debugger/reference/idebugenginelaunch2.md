---
title: IDebugEngineLaunch2 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4f052e640b479b51a4dff512a885ff17bf8cc7c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816867"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

起動し、プログラムを終了するデバッグ エンジン (DE) で使用します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 このインターフェイスは、カスタム ポートで完全処理できません。 プロセスを起動するための特別な要件がある場合、カスタム DE によって実装されます。 これは通常、ケース、DE、インタープリターの一部であるし、デバッグ中のプロセスがスクリプト: インタープリターが最初に、起動する必要があると、スクリプトが読み込まれ、起動します。 ポートは、インタープリターを起動できますが、スクリプトは特別な処理 (つまり、DE がロールを持つ) 必要があります。 カスタム ポートを処理できないプログラムを起動するための一意の要件がある場合にのみ、このインターフェイスが実装されます。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスを呼び出してセッション デバッグ マネージャー (SDM)、SDM は、このインターフェイスを取得できる場合から、 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)インターフェイス (QueryInterface を使用)。 このインターフェイスを取得できる場合、DE が特別な要件し、起動、ポートではなくプログラムを起動するには、このインターフェイスを呼び出す、SDM を認識します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugEngineLaunch2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|デを使用して、プロセスを起動します。|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|再開では、実行を処理します。|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|プロセスが終了するかどうかを決定します。|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|プロセスを終了します。|  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)

