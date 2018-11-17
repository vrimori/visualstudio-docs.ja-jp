---
title: GetScheduledTasksForDebugger メソッド |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3041d21a19ad276ed51e5fdcb9f11ad5468888bd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810066"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger メソッド
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

すべてのスケジュールされたタスクの配列を取得します。  
  
 **名前空間:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** mscorlib (mscorlib.dll 内)  
  
 .NET Framework からこの内部メンバーにアクセスできないため、次の構文には共通中間言語 (CIL) が提供されます。  
  
## <a name="syntax"></a>構文  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## <a name="return-value"></a>戻り値  
 スケジュールされたすべてのタスクの配列。 各タスクが実行か、または実行が完了します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドはスレッド セーフでないしの他のインスタンスと同時に使用する必要があります<xref:System.Threading.Tasks.TaskScheduler>デバッガーがその他のすべてのスレッドを中断された場合にのみには、デバッガーから呼び出すことはできます。  
  
## <a name="see-also"></a>関連項目  
 [TaskScheduler クラス](../../extensibility/debugger/taskscheduler-class-internal-members.md)

