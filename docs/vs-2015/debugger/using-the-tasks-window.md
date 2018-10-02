---
title: '[タスク] ウィンドウを使用して |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7e5d4c979d8160e9b2a9cee1a937bcc8049fc5b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548983"
---
# <a name="using-the-tasks-window"></a>[タスク] ウィンドウの使用
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[タスク ウィンドウを使用して](https://docs.microsoft.com/visualstudio/debugger/using-the-tasks-window)します。  
  
**タスク**ウィンドウに似ています、**スレッド**ウィンドウには、it に関する情報が表示されます<xref:System.Threading.Tasks.Task?displayProperty=fullName>、 [task_handle](http://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7)、または[WinJS.Promise](http://msdn.microsoft.com/library/windows/apps/br211867.aspx)各スレッドではなくオブジェクト。 スレッドと同様、タスクは、同時に実行できる非同期操作を表します。ただし、複数のタスクが同じスレッドで実行される場合もあります。 参照してください[JavaScript (Windows ストア アプリ) での非同期プログラミング](http://msdn.microsoft.com/library/windows/apps/hh700330.aspx)詳細についてはします。  
  
 マネージ コードで使用することができます、**タスク**を操作するときにウィンドウ<xref:System.Threading.Tasks.Task?displayProperty=fullName>オブジェクト、または、 **await**と**非同期**キーワード (**のAwait**と**Async** visual Basic で)。 マネージ コードでタスクの詳細については、次を参照してください。[並列プログラミング](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)します。  
  
 ネイティブ コードで使用することができます、**タスク**を操作するときにウィンドウ[タスク グループ](http://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077)、[並列アルゴリズム](http://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473)、[非同期エージェント](http://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a)と[軽量タスク](http://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90)します。 ネイティブ コードでタスクの詳細については、次を参照してください。[同時実行ランタイム](http://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)します。  
  
 JavaScript では、promise.then コードを操作するときに [タスク] ウィンドウを使用できます。  
  
 使用することができます、**タスク**デバッガーを中断する場合は、常にします。 上でアクセスできる、**デバッグ**メニューをクリックして**Windows**  をクリックし、**タスク**します。 次の図は、**タスク**ウィンドウの既定のモードにします。  
  
 ![並列タスク ウィンドウ](../debugger/media/parallel-tasks-window.png "Parallel_Tasks_Window")  
  
> [!NOTE]
>  マネージド コードでは、マネージド スレッドがスリープ状態または結合状態のとき、状態が <xref:System.Threading.Tasks.Task>、<xref:System.Threading.Tasks.TaskStatus>、または <xref:System.Threading.Tasks.TaskStatus> の <xref:System.Threading.Tasks.TaskStatus> は [タスク] ウィンドウに表示されないことがあります。  
  
## <a name="tasks-column-information"></a>[タスク] ウィンドウの列の情報  
 内の列、**タスク**ウィンドウは、次の情報を表示します。  
  
|列名|説明|  
|-----------------|-----------------|  
|**フラグ**|どのタスクにフラグが設定されているかを示します。タスクのフラグを設定または解除することができます。|  
|**アイコン**|黄色の矢印は現在のタスクを示します。 現在のタスクは、現在のスレッドの最上位のタスクです。<br /><br /> 白い矢印は中断しているタスク、つまりデバッガーを呼び出したときに現在のタスクだったタスクを示します。<br /><br /> 一時停止アイコンはユーザーによって凍結されているタスクを示します。 一覧でタスクを右クリックして、タスクを凍結したり凍結解除したりすることができます。|  
|**ID**|タスクに対してシステムで指定された番号です。 ネイティブ コードでは、タスクのアドレスになります。|  
|**状態**|タスクの現在の状態 (スケジュール、アクティブ、デッドロック、待機中、または完了) です。 スケジュール状態のタスクは、まだ実行されていないため、まだ呼び出し履歴、割り当てられたスレッド、関連情報がないタスクです。<br /><br /> アクティブなタスクは、デバッガーを中断する前にコードを実行していたタスクです。<br /><br /> 待機中のタスクは、イベントがシグナル状態になるか、ロックが解放されるか、別のタスクが終了するのを待機しているためにブロックされているタスクです。<br /><br /> デッドロック状態のタスクは、スレッドが別のスレッドでデッドロックされた待機中のタスクです。<br /><br /> ポインターを合わせる、**状態**ブロックに関する詳細を表示、デッドロックや待機中タスクのセル。 **警告:** 、**タスク**ウィンドウのみ待機チェーン トラバーサル (WCT) でサポートされる同期プリミティブを使用するブロックされているタスクのデッドロックが報告されます。 デッドロック状態の例では、<xref:System.Threading.Tasks.Task>オブジェクトで、デバッガーの報告、WCT を使用して**待機中デッドロック**します。 WCT を使用しない、同時実行ランタイムによって管理されるデッドロック状態のタスクについて、デバッガーの報告**待機している**します。 WCT の詳細については、次を参照してください。 [Wait Chain Traversal](http://msdn.microsoft.com/library/ms681622\(VS.85\).aspx)します。|  
|**開始時刻**|タスクがアクティブになった時間です。|  
|**期間**|タスクがアクティブになっている秒数です。|  
|**完了時刻**|タスクが完了した時間です。|  
|**場所**|タスクの呼び出し履歴内の現在の位置です。 タスクのすべての呼び出し履歴を表示するには、このセルの上にカーソルを置きます。 スケジュール状態のタスクについては、このセルには値が表示されません。|  
|**Task**|最初のメソッドと、作成時にタスクに渡された引数です。|  
|**Parent**|このタスクを作成したタスクの ID です。 この列が空白のタスクには親はありません。 これは、マネージド プログラムの場合にのみ適用されます。|  
|**スレッドの割り当て**|タスクを実行しているスレッドの ID と名前です。|  
|**戻り値の状態**|タスクが完了したときのステータスです。 状態の戻り値は**成功**、 **Cancelled**、および**エラー**します。|  
|**AppDomain**|マネージド コード用の情報で、タスクを実行しているアプリケーション ドメインを示します。|  
|**task_group**|ネイティブ コードのアドレスに対して、 [task_group](http://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7)タスクがスケジュールされているオブジェクト。 非同期エージェントおよび軽量タスクでは、この列は 0 に設定されます。|  
|プロセス|タスクが実行されているプロセスの ID です。|  
|Async State (非同期状態)|タスクの状態です (マネージド コードの場合)。 既定では、この列は非表示になっています。 この列を表示するには、いずれかの列ヘッダーのコンテキスト メニューを開きます。 選択**列**、 **AsyncState**します。|  
  
 ビューに列を追加するには、列見出しを右クリックし、追加する列を選択します (列を削除するには選択を解除します)。また、列を左右にドラッグして列の順序を変更することもできます。 列のショートカット メニューを次の図に示します。  
  
 ![並列タスク ウィンドウのショートカット ビュー メニュー](../debugger/media/parallel-tasks-contextmenu.png "Parallel_Tasks_ContextMenu")  
  
## <a name="sorting-tasks"></a>タスクの並べ替え  
 列を基準にタスクを並べ替えるには、列ヘッダーをクリックします。 たとえばをクリックして、 **ID**列ヘッダーをタスクをタスク ID を並べ替えることができます: 1,2,3,4,5 という具合です。 並べ替え順序を逆にするには、もう一度列ヘッダーをクリックします。 現在の並べ替え列と並べ替え順序は、列に矢印で示されます。  
  
## <a name="grouping-tasks"></a>タスクのグループ化  
 リスト ビューの任意の列に基づいてタスクをグループ化することができます。 などを右クリックし、**状態**列ヘッダーをクリックし、**状態でグループ化**、状態が同じすべてのタスクをグループ化することができます。 このようにすると、たとえば待機中のタスクをすばやく表示して、ブロックされている理由を集中的に確認することができます。 また、デバッグ セッションでは関係のないグループを折りたたむこともできます。 他の列を基準にしても、同じようにしてグループ化できます。 グループに対しては、グループ ヘッダーの横にあるボタンをクリックするだけで、まとめてフラグを設定したり解除したりすることができます。 次の図は、**タスク**グループ化されたモードでのウィンドウ。  
  
 ![並列タスク ウィンドウでグループ化されたモード](../debugger/media/parallel-tasks-groupedmode.png "Parallel_Tasks_GroupedMode")  
  
## <a name="parent-child-view"></a>親子ビュー  
 このビューは、マネージド コードの場合のみ使用できます。列見出しを右クリックし、をクリックして**親子ビュー**、すべての子タスクがサブノードを表示したり、その親の下の階層ビューにタスクの一覧を変更することができます。 次の図は、親子ビューでのタスクの表示を示しています。  
  
 ![親&#45;並列タスク ウィンドウの子ビュー](../debugger/media/parallel-tasks-parentchildview.png "Parallel_Tasks_ParentChildView")  
  
## <a name="flagging-tasks"></a>タスクに対するフラグの設定  
 項目を選択して、タスクを選択して、タスクが実行されるタスクを一覧表示するスレッドのフラグを設定することができます**フラグ**コンテキスト メニューから、または最初の列でフラグ アイコンをクリックします。 複数のタスクにフラグを設定してそれらだけを集中して確認する場合、フラグ列で並べ替えを行うことで、フラグを設定したすべてのタスクが上に表示されるようにすることができます。 使用することも、**並列スタック**を表示するウィンドウのタスクのみフラグが設定されます。 これにより、デバッグには関係のないタスクを除外することができます。 フラグはデバッグ セッション間で保持されません。  
  
## <a name="freezing-and-thawing-tasks"></a>タスクの凍結と凍結解除  
 タスク一覧の項目を右クリックし、をクリックして、タスクが実行されているスレッドを凍結する**割り当てられたスレッドを凍結**します。 (タスクが既に固定されている場合、コマンドは**割り当てられたスレッドの凍結解除**)。スレッドを凍結すると、現在のブレークポイントの後のコードのステップ実行でそのスレッドが実行されなくなります。 **固定すべてのスレッドがこの**コマンドは、タスク一覧の項目を実行している 1 つを除くすべてのスレッドを凍結します。  
  
 各タスクのその他のメニュー項目を次の図に示します。  
  
 ![並列タスク ウィンドウのショートカット スレッド メニュー](../debugger/media/parallel-tasks-contextmenu2.png "Parallel_Tasks_ContextMenu2")  
  
## <a name="see-also"></a>関連項目  
 [デバッガーの基本事項](../debugger/debugger-basics.md)   
 [マネージド コードをデバッグする](../debugger/debugging-managed-code.md)   
 [並列プログラミング](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [コンカレンシー ランタイム](http://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)   
 [並列スタック ウィンドウの使用](../debugger/using-the-parallel-stacks-window.md)   
 [チュートリアル: 並行アプリケーションのデバッグ](../debugger/walkthrough-debugging-a-parallel-application.md)



