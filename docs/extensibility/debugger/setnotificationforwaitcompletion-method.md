---
title: SetNotificationForWaitCompletion メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a005ee7d624604dd716042bd839b48b7a367dd48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion メソッド
設定または TASK_STATE_WAIT_COMPLETION_NOTIFICATION 状態ビットをクリアします。  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** (mscorlib.dll) の mscorlib  
  
## <a name="syntax"></a>構文  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `enabled`  
  
 `true` ビットを設定するには`false`未設定の状態ビットです。  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>コメント  
 デバッガーは、非同期メソッドの本体からのステップに役立つこのビットを設定します。 場合`enabled`は`true`、まだ完了されていないタスクにのみ、このメソッドを呼び出す必要があります。 場合`enabled`は`false`、完了したタスクで、このメソッドを呼び出すことができます。 いずれの場合にのみ使用してください promise スタイル タスク。  
  
## <a name="requirements"></a>要件  
  
## <a name="see-also"></a>関連項目  
 [Task クラス](../../extensibility/debugger/task-class-internal-members.md)