---
title: GetScheduledTasksForDebugger メソッド |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b68f8f238c180d4152d99b42f8ac075ef6dd3e7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54990629"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger メソッド
すべてのスケジュールされたタスクの配列を取得します。  
  
 **名前空間:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** mscorlib (で*mscorlib.dll*)  
  
 .NET Framework からこの内部メンバーにアクセスできないため、次の構文には共通中間言語 (CIL) が提供されます。  
  
## <a name="syntax"></a>構文  
  
```csharp  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## <a name="return-value"></a>戻り値  
 スケジュールされたすべてのタスクの配列。 各タスクが実行か、または実行が完了します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、スレッド セーフであると同時の他のインスタンスを使用しないでください<xref:System.Threading.Tasks.TaskScheduler>します。 デバッガーがその他のすべてのスレッドを中断された場合にのみ、デバッガーからこのメソッドを呼び出します。  
  
## <a name="see-also"></a>関連項目  
 [TaskScheduler クラス](../../extensibility/debugger/taskscheduler-class-internal-members.md)