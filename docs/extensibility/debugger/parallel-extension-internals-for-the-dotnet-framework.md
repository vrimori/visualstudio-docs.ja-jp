---
title: .NET Framework の拡張機能の内部の並列 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4936efe50023ed1e193d0c2ec0d9c3423ac5cc64
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100612"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>.NET Framework の並列拡張機能の内部
このセクションでは、内部の型、メソッドをについて説明し、できるようにするクラスのフィールドは、.NET framework の並列拡張機能のカスタムのデバッガーを実装します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Task クラス](../../extensibility/debugger/task-class-internal-members.md)  
 内部データ メンバーについて説明します、<xref:System.Threading.Tasks.Task?displayProperty=fullName>クラスです。  
  
 [TaskScheduler クラス](../../extensibility/debugger/taskscheduler-class-internal-members.md)  
 内部データ メンバーについて説明します、<xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>クラスです。  
  
 [ContingentProperties クラス](../../extensibility/debugger/contingentproperties-class-internal-members.md)  
 内部データ メンバーについて説明します、`System.Threading.Tasks.ContingentProperties`クラスです。  
  
 [AsyncTaskMethodBuilder 構造体](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)  
 内部メンバーを示します、<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>構造体。  
  
 [AsyncTaskMethodBuilder\<TResult > 構造体](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 内部メンバーを示します、<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>構造体。  
  
 [AsyncVoidMethodBuilder 構造体](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 内部メンバーを示します、<xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>構造体。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Visual Studio デバッガー拡張機能](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [並列プログラミング](/dotnet/standard/parallel-programming/index)