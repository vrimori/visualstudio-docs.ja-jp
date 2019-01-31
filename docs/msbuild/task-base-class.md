---
title: Task 基本クラス | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 6c3f6238-b9f0-4325-b8b0-de61090bd0a2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1859694a85b25effe56afef17f65bd831a65882
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959409"
---
# <a name="task-base-class"></a>Task 基本クラス
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
  
## <a name="see-also"></a>関連項目  
 [タスク リファレンス](../msbuild/msbuild-task-reference.md)   
 [タスク](../msbuild/msbuild-tasks.md)