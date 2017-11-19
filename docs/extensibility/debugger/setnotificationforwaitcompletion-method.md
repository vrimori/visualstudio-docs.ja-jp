---
title: "SetNotificationForWaitCompletion メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 385ae98e90d8f3a466c0983405c367347bb8ca10
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion メソッド
設定または TASK_STATE_WAIT_COMPLETION_NOTIFICATION 状態ビットをクリアします。  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** (mscorlib.dll) の mscorlib  
  
## <a name="syntax"></a>構文  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `enabled`  
  
 `true`ビットを設定するには`false`未設定の状態ビットです。  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>コメント  
 デバッガーは、非同期メソッドの本体からのステップに役立つこのビットを設定します。 場合`enabled`は`true`、まだ完了されていないタスクにのみ、このメソッドを呼び出す必要があります。 場合`enabled`は`false`、完了したタスクで、このメソッドを呼び出すことができます。 いずれの場合にのみ使用してください promise スタイル タスク。  
  
## <a name="requirements"></a>要件  
  
## <a name="see-also"></a>関連項目  
 [Task クラス](../../extensibility/debugger/task-class-internal-members.md)