---
title: タスク一覧の使用
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3a0fb071186d816e852c695ffe1cceed29d23ff8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="using-the-task-list"></a>タスク一覧の使用

**[タスク一覧]** を使って、 `TODO` 、 `HACK`などのトークンやカスタム トークンを使用するコード コメントを追跡し、コード内の事前に定義された場所に直接アクセスできるショートカットを管理できます。 ソース コード内のその場所に移動するには、一覧の項目をクリックします。

## <a name="the-task-list-window"></a>[タスク一覧] ウィンドウ

**[タスク一覧]** が開き、アプリケーション ウィンドウの下部に表示されます。

### <a name="to-open-the-task-list"></a>[タスク一覧] を開くには

- **[表示]** メニューで、**[タスク一覧]** をクリックします (キーボード: Ctrl + \\、T)。

    ![[タスク一覧] ウィンドウ](../ide/media/vs2015_task_list.png "vs2015_task_list")

### <a name="to-change-the-sort-order-of-the-list"></a>一覧の並べ替え順序を変更するには

- 任意の列のヘッダーをクリックします。 検索結果をさらに絞り込むには、Shift キーを押しながら 2 番目の列ヘッダーをクリックします。

     または、ショートカット メニューで、 **[並べ替え]** をクリックして、ヘッダーを選択します。 検索結果をさらに絞り込むには、Shift キーを押しながら 2 番目のヘッダーをクリックします。

### <a name="to-show-or-hide-columns"></a>列の表示/非表示を切り替えるには

- ショートカット メニューで、 **[列の表示]** をクリックします。 表示または非表示にする列をクリックします。

### <a name="to-change-the-order-of-the-columns"></a>列の順序を変更するには

- 任意の列ヘッダーを目的の場所にドラッグします。

## <a name="user-tasks"></a>ユーザー タスク

Visual Studio 2015 以降、ユーザー タスク機能が削除されています。 Visual Studio 2013 以前のバージョンからのユーザー タスク データを含むソリューションを開くと、.suo ファイル内のユーザー タスク データは影響を受けませんが、ユーザー タスクはタスク一覧に表示されません。

ユーザー タスク データに引き続きアクセスして更新する場合は、プロジェクトを Visual Studio 2013 で開き、好きなプロジェクト管理ツール (Team Foundation Server など) にユーザー タスクの内容をコピーする必要があります。

## <a name="tokens-and-comments"></a>トークンとコメント

**[タスク一覧]** ウィンドウには、コメント マーカーが手前にあるコードのコメント、および定義済みのトークンも表示されます。 たとえば、次の C# コメントには 3 つの個別の部分があります。

- コメント マーカー (`//`)

- トークン、たとえば (`TODO`)

- コメント (残りのテキスト)

```csharp
// TODO: Load state from previously suspended application
```

`TODO` が事前に定義されたトークンであるため、このコメントは `TODO` タスクとして一覧に表示されます。

###  <a name="customTokens"></a> カスタム トークン

既定で、Visual Studio には、HACK、TODO、UNDONE、NOTE のトークンが含まれます。 大文字と小文字は区別されません。

カスタム トークンを独自に作成することもできます。

#### <a name="to-create-a-custom-token"></a>カスタム トークンを作成するには

1. **[ツール]** メニューの **[オプション]** をクリックします。

2. **[環境]** フォルダーを開き、 **[タスク一覧]** をクリックします。

     [[タスク一覧] オプション ページ](../ide/reference/task-list-environment-options-dialog-box.md)が表示されます。

     ![Visual Studio タスク一覧](../ide/media/vs2015_task_list_options.png "vs2015_task_list_options")

3. **[トークン]** カテゴリの **[名前]** テキスト ボックスに、トークン名を入力します (例: バグ)。

4. **[優先順位]** ドロップダウン リストで、新しいトークンの既定の優先順位を選択します。 **[追加]** ボタンをクリックします。

###  <a name="cppComments"></a> C++ TODO コメント

既定で、C++ TODO コメントは **[タスク一覧]** ウィンドウに表示されます。 この動作を変更できます。

#### <a name="to-turn-off-c-todo-comments"></a>C++ TODO コメントをオフにするには

**[ツール]** メニューで、**[オプション]** > **[テキストエディター]** > **[C/C++]** > **[表示]** > **[コメント タスクの列挙]** の順に選択し、値を False に設定します。

## <a name="shortcuts"></a>ショートカット

*ショートカット* は、 **[タスク一覧]** で追跡されるコード内のブックマークで、標準のブックマークとはアイコンが異なります。 コード内の対応する位置に移動するには、 **[タスク一覧]** にあるショートカットをダブルクリックします。

![Visual Studio タスク一覧へのショートカット アイコン](../ide/media/vs2015_task_list_bookmark.png "vs2015_task_list_bookmark")

### <a name="to-create-a-shortcut"></a>ショートカットを作成するには

ショートカットを作成するには、ショートカットを配置するコードにポインターを挿入します。 **[編集]** > **[ブックマーク]** > **[タスク一覧へのショートカットの追加]** の順に選択するか、または **Ctrl** + **K**、**Ctrl** + **H** キーを押します。

コード内のショートカットをナビゲートしていくには、一覧でショートカットを選択し、ショートカット メニューから **[次のタスク]** か **[前のタスク]** をクリックします。

## <a name="see-also"></a>関連項目

- [[タスク一覧] ([オプション] ダイアログ ボックス - [環境])](../ide/reference/task-list-environment-options-dialog-box.md)