---
title: m_stateFlags フィールド |Microsoft Docs
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
ms.openlocfilehash: ee0cdebe00acce67fc9032a4ba9e7e566ecd9786
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232079"
---
# <a name="mstateflags-field"></a>m_stateFlags フィールド
現在の状態に関する情報を格納、<xref:System.Threading.Tasks.Task>オブジェクト。  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** mscorlib (で*mscorlib.dll*)  
  
 .NET Framework からこの内部メンバーにアクセスできないため、次の構文には共通中間言語 (CIL) が提供されます。  
  
## <a name="syntax"></a>構文  
  
```csharp  
.field assembly int32 modreq(System.Runtime.CompilerServices.IsVolatile) m_stateFlags  
```  
  
## <a name="remarks"></a>Remarks  
 通常、使用、<xref:System.Threading.Tasks.Task.Status%2A?displayProperty=fullName>プロパティをこの値にアクセスします。  
  
 このメンバーは、次の値の任意の組み合わせを指定できます。  
  
-   [TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)  
  
-   [TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)  
  
-   [TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)  
  
-   [TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)  
  
-   [TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)  
  
## <a name="see-also"></a>関連項目  
 [Task クラス](../../extensibility/debugger/task-class-internal-members.md)