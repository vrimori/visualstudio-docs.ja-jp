---
title: "Task クラスの内部メンバー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b92a622b6b898c917710ac748b9205079d71ea5e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="task-class---internal-members"></a>Task クラスの内部メンバー
このトピックの内容の内部のメンバーの説明、<xref:System.Threading.Tasks.Task?displayProperty=fullName>役立つクラスがカスタムのデバッガーを実装します。 このクラスの概要については、次を参照してください。、<xref:System.Threading.Tasks.Task>リファレンス トピックを参照します。  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** (mscorlib.dll) の mscorlib  
  
 .NET Framework からこれらの内部のメンバーにアクセスすることはできません、ため、次の構文は共通中間言語 (CIL) に提供されます。  
  
## <a name="syntax"></a>構文  
  
```  
.class public auto ansi System.Threading.Tasks.Task  
       extends System.Object  
       implements System.Threading.IThreadPoolWorkItem,  
                  System.IAsyncResult,  
                  System.IDisposable,  
                  System.Threading.ICancelableOperation  
```  
  
## <a name="members"></a>メンバー  
  
### <a name="methods"></a>メソッド  
  
|名前|説明|  
|----------|-----------------|  
|[SetNotificationForWaitCompletion メソッド](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|設定または TASK_STATE_WAIT_COMPLETION_NOTIFICATION 状態ビットをクリアします。|  
|[NotifyDebuggerOfWaitCompletion メソッド](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|デバッガーでブレークポイント ターゲットとして使用されるプレース ホルダー メソッドです。|  
  
### <a name="fields"></a>フィールド  
  
|name|説明|  
|----------|-----------------|  
|[m_action](../../extensibility/debugger/m-action-field.md)|実行するコードを表すデリゲート、<xref:System.Threading.Tasks.Task>オブジェクト。|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|その他のプロパティを格納、<xref:System.Threading.Tasks.Task>オブジェクト。|  
|[m_parent](../../extensibility/debugger/m-parent-field.md)|バッキング フィールド、<xref:System.Threading.Tasks.Task?displayProperty=fullName>プロパティの親です。|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|現在の状態に関する情報を格納、<xref:System.Threading.Tasks.Task>オブジェクト。|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|アクションによって使用されるデータを表すオブジェクト。|  
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|バッキング フィールド、<xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName>プロパティです。|  
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|[次へ] の使用可能な識別子、<xref:System.Threading.Tasks.Task>オブジェクト。|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|実行中の状態に到達する前に、タスクがキャンセルされたことか、タスクの取り消しを受領した例外なく完了したことを示します。|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|タスクが実行されていることを示します。|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|未処理の例外によって、タスクが完了したことを示します。|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|タスクが実行を正常に完了したことを示します。|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|タスクがそのデリゲートの実行が完了したが、アタッチされた子タスクの完了を暗黙的に待機していることを示します。|  
  
## <a name="remarks"></a>コメント  
 入口をマークするため、内部メソッドはデバッガー エンジンに役立つ<xref:System.Threading.Tasks.Task>コードの実行。  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>参照  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [.NET Framework の並列拡張機能の内部](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)