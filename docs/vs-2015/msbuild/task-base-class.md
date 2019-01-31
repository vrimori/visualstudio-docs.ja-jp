---
title: Task 基本クラス | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 6c3f6238-b9f0-4325-b8b0-de61090bd0a2
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 041b57c252ffe77dc7374b39ba40b8152a390205
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54778738"
---
# <a name="task-base-class"></a>Task 基本クラス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
多くのタスクが最終的に <xref:Microsoft.Build.Utilities.Task> クラスから継承します。 このクラスは、それから派生するタスクにいくつかのパラメーターを追加します。 このドキュメントでは、これらのパラメーターを示します。  
  
## <a name="parameters"></a>パラメーター  
 この基本クラスのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|省略可能な <xref:Microsoft.Build.Framework.IBuildEngine> 型のパラメーターです。<br /><br /> タスクで使用できるビルド エンジン インターフェイスを指定します。 ビルド エンジンは、自動的にこのパラメーターを設定して、タスクによるコールバックを可能にします。|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|省略可能な <xref:Microsoft.Build.Framework.IBuildEngine2> 型のパラメーターです。<br /><br /> タスクで使用できるビルド エンジン インターフェイスを指定します。 ビルド エンジンは、自動的にこのパラメーターを設定して、タスクによるコールバックを可能にします。<br /><br /> この便利なプロパティにより、このクラスから継承するタスクの作成者は、`IBuildEngine2` から `IBuildEngine` に値をキャストする必要がなくなります。|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|省略可能な <xref:Microsoft.Build.Framework.IBuildEngine3> 型のパラメーターです。<br /><br /> ホストによって提供されるビルド エンジン インターフェイスを指定します。|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|省略可能な <xref:Microsoft.Build.Framework.ITaskHost> 型のパラメーターです。<br /><br /> ホスト オブジェクト インスタンスを指定します (null も指定できます)。 ビルド エンジンは、ホスト IDE によってホスト オブジェクトがこの特定のタスクに関連付けられている場合にこのプロパティを設定します。|  
|<xref:Microsoft.Build.Utilities.Task.Log%2A>|省略可能な <xref:Microsoft.Build.Utilities.TaskLoggingHelper> 型の読み取り専用パラメーターです。<br /><br /> ログ ヘルパー オブジェクト。|  
  
## <a name="see-also"></a>「  
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)   
 [タスク](../msbuild/msbuild-tasks.md)
