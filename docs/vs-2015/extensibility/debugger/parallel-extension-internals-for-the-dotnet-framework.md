---
title: .NET Framework の拡張機能の内部を並列 |Microsoft Docs
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
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 88155d1c9cf55cb8f0397f0b737a77bd04dd2fa6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794960"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>.NET Framework の並列拡張機能の内部
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

内部の型、メソッド、について説明し、できるようにするクラスのフィールドは、.NET Framework の parallel extensions のカスタムのデバッガーを実装します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Task クラス](../../extensibility/debugger/task-class-internal-members.md)  
 内部データ メンバーについて説明します、<xref:System.Threading.Tasks.Task?displayProperty=fullName>クラス。  
  
 [TaskScheduler クラス](../../extensibility/debugger/taskscheduler-class-internal-members.md)  
 内部データ メンバーについて説明します、<xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>クラス。  
  
 [ContingentProperties クラス](../../extensibility/debugger/contingentproperties-class-internal-members.md)  
 内部データ メンバーについて説明します、`System.Threading.Tasks.ContingentProperties`クラス。  
  
 [AsyncTaskMethodBuilder 構造体](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)  
 内部メンバーについて説明します、<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>構造体。  
  
 [AsyncTaskMethodBuilder\<TResult > 構造体](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 内部メンバーについて説明します、<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>構造体。  
  
 [AsyncVoidMethodBuilder 構造体](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 内部メンバーについて説明します、<xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>構造体。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Visual Studio デバッガーの拡張性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [並列プログラミング](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)

