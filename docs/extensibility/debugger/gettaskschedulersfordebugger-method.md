---
title: GetTaskSchedulersForDebugger メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d5d0b78a4f115d1ba07848db914289c35034d465
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger メソッド
すべての配列を取得<xref:System.Threading.Tasks.TaskScheduler>現在アクティブなオブジェクトです。  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** (mscorlib.dll) の mscorlib  
  
 .NET Framework からこの内部のメンバーにアクセスすることはできません、ため、次の構文は共通中間言語 (CIL) に提供されます。  
  
## <a name="syntax"></a>構文  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>戻り値  
 すべての配列<xref:System.Threading.Tasks.TaskScheduler>これで現在アクティブなオブジェクト<xref:System.AppDomain>です。  
  
## <a name="remarks"></a>コメント  
 このメソッドはスレッド セーフであるの他のインスタンスと同時に使用しないで<xref:System.Threading.Tasks.TaskScheduler>です。 デバッガーには、他のすべてのスレッドが中断されている場合にのみ、デバッガーから呼び出すことはできます。  
  
## <a name="see-also"></a>関連項目  
 [TaskScheduler クラス](../../extensibility/debugger/taskscheduler-class-internal-members.md)