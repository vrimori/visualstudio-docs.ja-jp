---
title: Task クラス - 内部メンバー |Microsoft Docs
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
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a1fb04d3bc15fcac80cbe91d65a0d11ee9e71335
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218492"
---
# <a name="task-class---internal-members"></a>Task クラス - 内部メンバー
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックでの内部メンバーの説明、<xref:System.Threading.Tasks.Task?displayProperty=fullName>する際に役立つクラスがカスタムのデバッガーを実装します。 このクラスの詳細については、次を参照してください。、<xref:System.Threading.Tasks.Task>リファレンス トピック。  
  
 **名前空間:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** mscorlib (mscorlib.dll 内)  
  
 .NET Framework からこれらの内部メンバーにアクセスできないため、次の構文には共通中間言語 (CIL) が提供されます。  
  
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
|[NotifyDebuggerOfWaitCompletion メソッド](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|プレース ホルダー メソッドは、デバッガーがブレークポイント ターゲットとして使用します。|  
  
### <a name="fields"></a>フィールド  
  
|名前|説明|  
|----------|-----------------|  
|[m_action](../../extensibility/debugger/m-action-field.md)|実行するコードを表すデリゲート、<xref:System.Threading.Tasks.Task>オブジェクト。|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|その他のプロパティを格納、<xref:System.Threading.Tasks.Task>オブジェクト。|  
|[m_parent](../../extensibility/debugger/m-parent-field.md)|バッキング フィールドは、<xref:System.Threading.Tasks.Task?displayProperty=fullName>プロパティの親。|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|現在の状態に関する情報を格納、<xref:System.Threading.Tasks.Task>オブジェクト。|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|アクションによって使用されるデータを表すオブジェクト。|  
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|バッキング フィールドは、<xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName>プロパティ。|  
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|[次へ] の使用可能な識別子を<xref:System.Threading.Tasks.Task>オブジェクト。|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|実行中の状態に到達する前に、タスクがキャンセルされたこと、またはタスクの取り消しし、例外なく完了したことを示します。|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|タスクが実行されていることを示します。|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|未処理の例外によって、タスクが完了したことを示します。|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|タスクが実行を正常に完了したことを示します。|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|タスクがそのデリゲートの実行が完了したが、暗黙的にアタッチされた子タスクの完了を待機していることを示します。|  
  
## <a name="remarks"></a>Remarks  
 次の内部メソッドは、マークの入り口ので、デバッガー エンジンに便利です<xref:System.Threading.Tasks.Task>コードの実行。  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [.NET Framework の並列拡張機能の内部](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

