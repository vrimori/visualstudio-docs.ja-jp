---
title: SetNotificationForWaitCompletion メソッド |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c674057d57e5e89a6ed92f56df8606b1a0280fc2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54989446"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion メソッド
設定または TASK_STATE_WAIT_COMPLETION_NOTIFICATION 状態ビットをクリアします。  
  
 **名前空間:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** mscorlib (で*mscorlib.dll*)  
  
## <a name="syntax"></a>構文  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
### <a name="parameters"></a>パラメーター  
 `enabled`  
  
 `true` ビットを設定するには`false`未設定の状態ビット。  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>Remarks  
 デバッガーでは、非同期のメソッド本体の外部の手順を支援するには、このビットを設定します。 場合`enabled`は`true`、まだ完了されていないタスクにのみ、このメソッドを呼び出す必要があります。 ときに`enabled`は`false`、完了したタスクでこのメソッドを呼び出すことができます。 いずれの場合、その必要がありますのみ使用 promise スタイルのタスクの。  
  
## <a name="requirements"></a>必要条件  
  
## <a name="see-also"></a>関連項目  
 [Task クラス](../../extensibility/debugger/task-class-internal-members.md)