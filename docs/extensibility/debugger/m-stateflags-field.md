---
title: m_stateFlags フィールド |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_stateFlags field, Task class [.NET Framework debug engines]
ms.assetid: 82b20efc-08f2-4cd2-91f6-4e01e3da906b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8842b4e7a3b6c0cb13b0c0d446e0e03b525ae903
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31098122"
---
# <a name="mstateflags-field"></a>m_stateFlags フィールド
現在の状態に関する情報を格納、<xref:System.Threading.Tasks.Task>オブジェクト。  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** (mscorlib.dll) の mscorlib  
  
 .NET Framework からこの内部のメンバーにアクセスすることはできません、ため、次の構文は共通中間言語 (CIL) に提供されます。  
  
## <a name="syntax"></a>構文  
  
```  
.field assembly int32 modreq(System.Runtime.CompilerServices.IsVolatile) m_stateFlags  
```  
  
## <a name="remarks"></a>コメント  
 通常使用する、<xref:System.Threading.Tasks.Task.Status%2A?displayProperty=fullName>この値にアクセスするプロパティです。  
  
 このメンバーは、次の値の任意の組み合わせを指定できます。  
  
-   [TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)  
  
-   [TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)  
  
-   [TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)  
  
-   [TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)  
  
-   [TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)  
  
## <a name="see-also"></a>関連項目  
 [Task クラス](../../extensibility/debugger/task-class-internal-members.md)