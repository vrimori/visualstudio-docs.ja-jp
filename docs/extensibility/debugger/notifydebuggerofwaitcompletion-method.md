---
title: "NotifyDebuggerOfWaitCompletion メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d28b6d4eb18535cbfef39790b544288ad39659c3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion メソッド
デバッガーでブレークポイント ターゲットとして使用されるプレース ホルダー メソッドです。 このメソッドでは、インライン関数、または最適化されたは使用できません。  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** (mscorlib.dll) の mscorlib  
  
## <a name="syntax"></a>構文  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## <a name="remarks"></a>コメント  
 タスクですべての結合操作は、デバッガー通知ビットが設定されている場合、このメソッドを呼び出す必要があります。  
  
## <a name="requirements"></a>必要条件  
  
## <a name="see-also"></a>参照  
 [Task クラス](../../extensibility/debugger/task-class-internal-members.md)