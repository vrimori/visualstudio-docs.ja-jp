---
title: ".NET Framework の拡張機能の内部を並列 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c679d573bde8352906471b4eded7ccb9051f5959
ms.lasthandoff: 02/22/2017

---
# <a name="parallel-extension-internals-for-the-net-framework"></a>.NET Framework の並列拡張機能の内部
このセクションでは、内部の型、メソッドを説明し、役立つクラスのフィールドは、parallel extensions to .NET Framework 用のカスタムのデバッガーを実装します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Task クラス](../../extensibility/debugger/task-class-internal-members.md)  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>クラス</xref:System.Threading.Tasks.Task?displayProperty=fullName>の内部データ メンバーについて説明します  
  
 [TaskScheduler クラス](../../extensibility/debugger/taskscheduler-class-internal-members.md)  
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>クラス</xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>の内部データ メンバーについて説明します  
  
 [ContingentProperties クラス](../../extensibility/debugger/contingentproperties-class-internal-members.md)  
 内部データ メンバーについて説明します、`System.Threading.Tasks.ContingentProperties`クラスです。  
  
 [AsyncTaskMethodBuilder 構造体](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)  
 内部メンバーについて説明します、<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>構造体</xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>。  
  
 [AsyncTaskMethodBuilder\<TResult > 構造体](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 内部メンバーについて説明します、<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>構造体</xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>。  
  
 [AsyncVoidMethodBuilder 構造体](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 内部メンバーについて説明します、<xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>構造体</xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName></xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName></xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Visual Studio デバッガーの拡張性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [並列プログラミング](http://msdn.microsoft.com/Library/4d83c690-ad2d-489e-a2e0-b85b898a672d)
