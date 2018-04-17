---
title: IDebugProgramDestroyEventFlags2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f6b57206159ce00fbb79e9f9af1a6353588df76c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
既定の動作をオーバーライドするデバッグ エンジンを有効に、 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI デバッグ セッションを終了するとします。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 このインターフェイスは、デバッグ エンジンによって実装されます。 ホストを作成し、プロセスの有効期間にわたって複数のプログラムを破棄すると便利です。  
  
## <a name="methods"></a>メソッド  
 次の表は、メソッドの`IDebugProgramDestroyEventFlags2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|プログラムを取得するフラグを破棄します。|  
  
## <a name="remarks"></a>コメント  
 既定の動作、 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI がすべてのプログラムは、プログラムを送信した後に、デザイン モードに戻るにはイベントを破棄します。 このインターフェイスは、その動作を変更するデバッグ エンジンを使用します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll