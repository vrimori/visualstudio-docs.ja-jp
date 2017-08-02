---
title: "タスク一覧の使用 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
ms.assetid: f46a75a8-47b3-4cb6-bb59-b72e3356a664
caps.latest.revision: 29
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 01e8f3cc1bbcc2bc4b2fc94df1dad7d248b67290
ms.contentlocale: ja-jp
ms.lasthandoff: 02/22/2017

---
# <a name="using-the-task-list"></a>タスク一覧の使用
[ **タスク一覧** ] を使って、 `TODO` 、 `HACK`などのトークンやカスタム トークンを使用するコード コメントを追跡し、コード内の事前に定義された場所に直接アクセスできるショートカットを管理できます。 ソース コード内のその場所に移動するには、一覧の項目をクリックします。  
  
 このトピックの内容  
  
-   [[タスク一覧] ウィンドウ](../ide/using-the-task-list.md#taskListWindow)  
  
-   [ユーザー タスク](../ide/using-the-task-list.md#userTasks)  
  
-   [トークンとコメント](../ide/using-the-task-list.md#tokensComments)  
  
-   [カスタム トークン](../ide/using-the-task-list.md#customTokens)  
  
-   [C++ TODO コメント](../ide/using-the-task-list.md#cppComments)  
  
-   [ショートカット](../ide/using-the-task-list.md#shortcuts)  
  
##  <a name="taskListWindow"></a> [タスク一覧] ウィンドウ  
 **[タスク一覧]** が開き、アプリケーション ウィンドウの下部に表示されます。  
  
#### <a name="to-open-the-task-list"></a>[タスク一覧] を開くには  
  
-   **[表示]** メニューで、**[タスク一覧]** をクリックします (キーボード: Ctrl + \\、T)。  
  
     ![[タスク一覧] ウィンドウ](~/docs/ide/media/vs2015_task_list.png "vs2015_task_list")  
  
#### <a name="to-change-the-sort-order-of-the-list"></a>一覧の並べ替え順序を変更するには  
  
-   任意の列のヘッダーをクリックします。 検索結果をさらに絞り込むには、Shift キーを押しながら 2 番目の列ヘッダーをクリックします。  
  
     または、ショートカット メニューで、 **[並べ替え]**をクリックして、ヘッダーを選択します。 検索結果をさらに絞り込むには、Shift キーを押しながら 2 番目のヘッダーをクリックします。  
  
#### <a name="to-show-or-hide-columns"></a>列の表示/非表示を切り替えるには  
  
-   ショートカット メニューで、 **[列の表示]**をクリックします。 表示または非表示にする列をクリックします。  
  
#### <a name="to-change-the-order-of-the-columns"></a>列の順序を変更するには  
  
-   任意の列ヘッダーを目的の場所にドラッグします。  
  
##  <a name="userTasks"></a> ユーザー タスク  
 Visual Studio 2015 ではユーザー タスク機能が削除されました。 Visual Studio 2013 以前のバージョンからのユーザー タスク データを含むソリューションを Visual Studio 2015 で開くと、.suo ファイル内のユーザー タスク データは影響を受けませんが、ユーザー タスクはタスク一覧に表示されません。  
  
 ユーザー タスク データに引き続きアクセスして更新する場合は、プロジェクトを Visual Studio 2013 で開き、好きなプロジェクト管理ツール (Team Foundation Server など) にユーザー タスクの内容をコピーする必要があります。  
  
##  <a name="tokensComments"></a> トークンとコメント  
 **[タスク一覧]** ウィンドウには、コメント マーカーが手前にあるコードのコメント、および定義済みのトークンも表示されます。 たとえば、次の C# コメントには 3 つの個別の部分があります。  
  
-   コメント マーカー (`//`)  
  
-   トークン、たとえば (`TODO`)  
  
-   コメント (残りのテキスト)  
  
```  
// TODO: Load state from previously suspended application  
```  
  
 `TODO` が事前に定義されたトークンであるため、このコメントは `TODO` タスクとして一覧に表示されます。  
  
###  <a name="customTokens"></a> カスタム トークン  
 既定で、Visual Studio には、HACK、TODO、UNDONE、NOTE のトークンが含まれます。 大文字と小文字は区別されません。  
  
 カスタム トークンを独自に作成することもできます。  
  
##### <a name="to-create-a-custom-token"></a>カスタム トークンを作成するには  
  
1.  **[ツール]** メニューの **[オプション]**をクリックします。  
  
2.  **[環境]** フォルダーを開き、 **[タスク一覧]**をクリックします。  
  
     [[タスク一覧] ([オプション] ダイアログ ボックス - [環境])](../ide/reference/task-list-environment-options-dialog-box.md) が表示されます。  
  
     ![Visual Studio タスク一覧](~/docs/ide/media/vs2015_task_list_options.png "vs2015_task_list_options")  
  
3.  **[トークン]** カテゴリの **[名前]** テキスト ボックスに、トークン名を入力します (例: バグ)。  
  
4.  **[優先順位]** ドロップダウン リストで、新しいトークンの既定の優先順位を選択します。 **[追加]** ボタンをクリックします。  
  
###  <a name="cppComments"></a> C++ TODO コメント  
 既定で、C++ TODO コメントは **[タスク一覧]** ウィンドウに表示されます。 この動作を変更できます。  
  
##### <a name="to-turn-off-c-todo-comments"></a>C++ TODO コメントをオフにするには  
  
1.  **[ツール]** メニューで、**[オプション &#124; テキストエディター &#124; C/C++ &#124; 表示 &#124; コメント タスクの列挙]** に移動し、値を False に設定します。  
  
2.  **[オプション]** ダイアログ ボックスで、 **[テキスト エディター]**を開きます。  
  
3.  **[C/C++]**で **[表示]**を選択し、 **[コメント タスクの列挙]** を **[False]**に設定します。  
  
##  <a name="shortcuts"></a> ショートカット  
 *ショートカット* は、 **[タスク一覧]**で追跡されるコード内のブックマークで、標準のブックマークとはアイコンが異なります。 コード内の対応する位置に移動するには、 **[タスク一覧]** にあるショートカットをダブルクリックします。  
  
 ![Visual Studio タスク一覧へのショートカット アイコン](~/docs/ide/media/vs2015_task_list_bookmark.png "vs2015_task_list_bookmark")  
  
#### <a name="to-create-a-shortcut"></a>ショートカットを作成するには  
  
-   ショートカットを配置するコードにポインターを挿入します。 **[編集 &#124; ブックマーク &#124; タスク一覧へのショートカットの追加]** を選択するか、キーボードで Ctrl + K、Ctrl + H を押します。  
  
     コード内のショートカットをナビゲートしていくには、一覧でショートカットを選択し、ショートカット メニューから **[次のタスク]** か **[前のタスク]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [[タスク一覧] ([オプション] ダイアログ ボックス - [環境])](../ide/reference/task-list-environment-options-dialog-box.md)
