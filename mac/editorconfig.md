---
title: EditorConfig
description: EditorConfig ファイルを使用し、Visual Studio for Mac でプロジェクト コードを一貫性のあるスタイルで記述します。
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: 336ec5ef0779bcd67302bea7b51851dced531a7d
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>カスタム EditorConfig ファイルの作成と編集

Visual Studio for Mac では、[EditorConfig](http://editorconfig.org/) ファイルをプロジェクトまたはコードベースに追加して、そのコードベースを使用するすべてのユーザーに一貫したコーディング スタイルを使用させることができます。 EditorConfig ファイルで宣言された設定は、Visual Studio テキスト エディターのグローバルな設定より優先されます。 プロジェクトまたはコードベース内で EditorConfig を使用すると、プロジェクトのコード記述スタイル、優先設定、警告を設定できます。 Visual Studio for Mac の全ユーザーにとって、プロジェクトのコード記述慣例に従うことが楽になります。

[EditorConfig](http://editorconfig.org/) ファイルは、Visual Studio 2017 など、さまざまな IDE やコード エディターでサポートされています。 

## <a name="supported-settings"></a>サポートされる設定

Visual Studio のエディターは、[EditorConfig プロパティ](http://editorconfig.org/#supported-properties)の次のコア セットをサポートします。

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

EditorConfig は、C# の[コード スタイル書式設定](https://docs.microsoft.com/visualstudio/ide/editorconfig-code-style-settings-reference)にも対応しています。

## <a name="add-an-editorconfig-file-to-a-project"></a>EditorConfig ファイルをプロジェクトに追加する

### <a name="adding-a-new-editorconfig-file"></a>新しい EditorConfig ファイルを追加する

1. Visual Studio for Mac でプロジェクトを開きます。 ファイルを追加するプロジェクト ノードを選択します。

2. プロジェクト ノードを選択している状態で、メニュー バーから **[ファイル]、[新しいファイル]** の順に選択し、 **[新しいファイル]** ダイアログを開きます。

3. **[その他]、[空のテキスト ファイル]** の順に選択し、`.editorconfig` という **[名前]** を付けます。 **[新規作成]** を押してファイルを作成し、エディターで開きます。

    ![[新しいファイル] ダイアログ](media/editorconfig-image1.png)

4. ファイルを編集します。 例:

    ```EditorConfig
    # This file is the top-most EditorConfig file
    root = true

    # All Files
    [*]
    indent_style = space
    indent_size = 8
    insert_final_newline = false
    trim_trailing_whitespace = false

    [*.cs]
    csharp_new_line_before_open_brace = none
    ```

4. ファイルを追加しても、設定が自動的に更新されることはありません。 `.editorconfig` ファイルの設定を反映させるには、プロジェクト ノードを選択し、メニュー バーから **[編集]、[形式]、[ドキュメントのフォーマット]** の順に選択します。

    ![[ドキュメントのフォーマット] メニュー アイテム](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>既存の EditorConfig ファイルを追加する

`.editorconfig` ファイルが既に含まれているプロジェクトかソリューションを使用している場合、設定の適用に必要な作業はありません。 新しいコード行はすべて、EditorConfig の設定に従って書式設定されます。 Visual Studio for Mac はソリューション レベルで `.editorconfig` ファイルに従いますが、このファイルはソリューション パッドに表示されないことがあります。`.` で始まるファイルは macOS で隠しファイルになるためです。

プロジェクトの既存の `.editorconfig` ファイルを再利用すると便利な場合があります。 既存のファイルを追加するには、最初に**ターミナル**に次のコマンドを入力し、Finder に隠しファイルを表示する必要があります。

```bash
$ defaults write com.apple.Finder AppleShowAllFiles true
$ killall Finder
```

`.editorconfig` ファイルが表示されたら、それをプロジェクト ノードにドラッグします。 次のダイアログが表示されたら、**[ファイルをディレクトリにコピーする]** オプションを選択し、**[OK]** を選択します。

![[ドキュメントのフォーマット] メニュー アイテム](media/editorconfig-image3.png)

`.editorconfig` ファイルの設定を反映させるには、プロジェクト ノードを選択し、メニュー バーから **[編集]、[形式]、[ドキュメントのフォーマット]** の順に選択します。

## <a name="editing-an-editorconfig-file"></a>EditorConfig ファイルを編集する

EditorConfig ファイルでは、単純なファイル レイアウトを利用し、設定を指定します。前の例を利用して説明すると下のようになります。


```EditorConfig
# This file is the top-most EditorConfig file
root = true

# All Files
[*]
indent_style = space
indent_size = 4
insert_final_newline = false
trim_trailing_whitespace = false

[*.cs]
csharp_new_line_before_open_brace = none
```

`root` を `true` に設定すると、このファイルがコードベースの一番上のファイルとして設定され、プロジェクトでそれより上の `.editorconfig` ファイルは無視されます。詳細は「[EditorConfig 設定のオーバーライド](#override-editorconfig-settings)」セクションにあります。

各セクションには角括弧 (**[ ]**) が付き、後続のプロパティが付属するファイルの型に関する情報が指定されます。

上の例では、一部の設定がプロジェクトのすべてのファイルに適用されます。その他の設定は C# ファイルにのみ追加されます。 下のスクリーンショットでは、`.editorconfig` 設定の適用前後を確認できます。

**適用前**:

![EditorConfig 設定の適用前](media/editorconfig-image4.png)

**適用後**:

![EditorConfig 設定の適用後](media/editorconfig-image5.png)

利用できる EditorConfig 設定に関する詳細については、「[EditorConfig の .NET コーディング規則の設定](https://docs.microsoft.com/visualstudio/ide/editorconfig-code-style-settings-reference)」という記事と、公式ドキュメントの[サポート プロパティ](http://editorconfig.org/#supported-properties)に関するセクションを参照してください。

## <a name="override-editorconfig-settings"></a>EditorConfig 設定のオーバーライド

各ソリューションに複数の `.editorconfig` ファイルを与えることができます。 Visual Studio for Mac はソリューションで上から下へと `.editorconfig` ファイルを読み、読みながら設定を追加したり、オーバーライドしたりします。 つまり、編集しているファイルに "最も近い" `.editorconfig` の設定が優先されます。 

すべての上位レベルの `.editorconfig` ファイルからの設定がコードベースのこの部分に適用_されない_ようにするには、次のように `root=true` プロパティを下位レベルの `.editorconfig` ファイルに追加します。

```EditorConfig
# top-most EditorConfig file
root = true
```