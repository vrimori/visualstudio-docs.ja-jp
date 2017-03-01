---
title: "Task クラスの内部メンバー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: 14
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 21acb0a52dfde7ad565e9764e2a333a9925a2171
ms.lasthandoff: 02/22/2017

---
# <a name="task-class---internal-members"></a>Task クラスの内部メンバー
このトピックの内部メンバーの説明、<xref:System.Threading.Tasks.Task?displayProperty=fullName>役立つクラスは、カスタムのデバッガーを実装します</xref:System.Threading.Tasks.Task?displayProperty=fullName>。 このクラスの概要については、次を参照してください、<xref:System.Threading.Tasks.Task>リファレンス トピック。</xref:System.Threading.Tasks.Task> 。  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName></xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** (mscorlib.dll) の mscorlib  
  
 .NET Framework からこれらの内部メンバーにアクセスできないため、次の構文は共通中間言語 (CIL) に提供されます。  
  
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
|[NotifyDebuggerOfWaitCompletion メソッド](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|プレース ホルダー メソッドは、デバッガーのブレークポイント ターゲットとして使用します。|  
  
### <a name="fields"></a>フィールド  
  
|名前|説明|  
|----------|-----------------|  
|[m_action](../../extensibility/debugger/m-action-field.md)|実行するコードを表すデリゲート、<xref:System.Threading.Tasks.Task>オブジェクト</xref:System.Threading.Tasks.Task>。|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|追加のプロパティの格納、<xref:System.Threading.Tasks.Task>オブジェクト</xref:System.Threading.Tasks.Task>。|  
|[m_parent](../../extensibility/debugger/m-parent-field.md)|バッキング フィールド、<xref:System.Threading.Tasks.Task?displayProperty=fullName>プロパティの親</xref:System.Threading.Tasks.Task?displayProperty=fullName>。|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|現在の状態に関する情報を格納、<xref:System.Threading.Tasks.Task>オブジェクト</xref:System.Threading.Tasks.Task>。|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|アクションによって使用されるデータを表すオブジェクト。|  
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|バッキング フィールド、<xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName>プロパティ</xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName>。|  
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|次の使用可能な識別子を<xref:System.Threading.Tasks.Task>オブジェクト</xref:System.Threading.Tasks.Task>。|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|実行中の状態に達する前に、タスクがキャンセルされたこと、またはタスクがその取り消しし、例外なしで完了を示します。|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|タスクが実行されていることを示します。|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|未処理の例外によって、タスクが完了したことを示します。|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|タスクが実行を正常に完了したことを示します。|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|タスクが、デリゲートの実行が完了したが、暗黙的にアタッチされた子タスクの完了を待機していることを示します。|  
  
## <a name="remarks"></a>コメント  
 次の内部メソッドは、入り口をマークするため、デバッガーのエンジンに役立つ<xref:System.Threading.Tasks.Task>コードの実行:</xref:System.Threading.Tasks.Task>  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName></xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [.NET Framework の並列拡張機能の内部](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
