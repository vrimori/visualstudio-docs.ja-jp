---
title: "Visual Studio での EditorConfig 設定の使用 | Microsoft Docs"
ms.custom: 
ms.date: 10/27/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editorconfig [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-general
ms.openlocfilehash: 39b3228e64257552c8b629e421c9b5aa4f0e0931
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/29/2017
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>EditorConfig で移植可能なカスタム エディター設定を作成する

Visual Studio のテキスト エディター設定は、指定された型のすべてのプロジェクトに適用されます。 そのため、たとえば、C# テキスト エディター設定を変更した場合、その設定は Visual Studio の*すべて*の C# プロジェクトに適用されます。 ただし、自分の好みのエディター設定とは異なる規則を使用しなければならないこともあります。 これを可能にするのが [EditorConfig](http://editorconfig.org/) ファイルであり、プロジェクトごとに、インデント サイズなどの一般的なテキスト エディター オプションを記述することができます。 コードおよびプロジェクト ファイルと共に存在する .editorconfig ファイルに含まれている EditorConfig 設定は、Visual Studio テキスト エディターのグローバル設定より優先されます。 つまり、そのプロジェクトに固有のテキスト エディター設定を使用するように各コードベースを調整できます。 Visual Studio でこの機能を使用するためのプラグインは必要ありません。

## <a name="coding-consistency"></a>コーディングの一貫性

EditorConfig ファイルの設定を利用すれば、使用するエディターや IDE に関係なく、コードベースでコーディングのスタイルと設定の一貫性を維持できます。たとえば、インデントのスタイル、タブの幅、行末文字、エンコードなどです。 たとえば、C# でコーディングするとき、インデントを常に 5 つ分の空白文字で構成し、文書で UTF-8 エンコードを使用し、各行が常に CR/LF で終わるというという慣習をコードベースに与えるのであれば、そのように .editorconfig ファイルを構成できます。

個人的なプロジェクトで使用するコーディング規則は、チームのプロジェクトで使用するそれとは変えることができます。 たとえば、コーディングの際に、自分はインデントでタブ文字を追加したくても、 チームはインデントでタブ文字ではなく 4 つの空白文字を追加したいかもしれません。 EditorConfig ファイルがこの問題を解決します。シナリオごとに構成を与えることができるからです。

設定はコードベースのファイルに含まれているため、そのコードベースと共に移動します。 EditorConfig 対応のエディターでコード ファイルを開く限り、テキスト エディター設定が実装されます。 EditorConfig ファイルの詳細については、[EditorConfig.org](http://editorconfig.org/) Web サイトをご覧ください。

## <a name="override-editorconfig-settings"></a>EditorConfig 設定を上書きする

ファイル階層のフォルダーに .editorconfig ファイルを追加すると、その設定がその階層レベルとその下のレベルのあらゆる該当ファイルに適用されます。 特定のプロジェクトまたはコードベースが最上位の EditorConfig ファイルとは異なる規則を使用するように、EditorConfig 設定を上書きする場合は、コードベースのリポジトリまたはプロジェクト ディレクトリのルートに .editorconfig ファイルを追加するだけです。 Visual Studio がそのディレクトリ構造より上にある .editorconfig ファイルを検索しないように、ファイルに ```root=true``` プロパティを必ず配置します。 新しい EditorConfig ファイル設定は、同じレベルと任意のサブディレクトリ内のファイルに適用されます。

```
# top-most EditorConfig file
root = true
```

![EditorConfig 階層](../ide/media/vside_editorconfig_hierarchy.png)

EditorConfig ファイルは上から下に読み取られ、最も近い EditorConfig ファイルが最後に読み取られます。 一致する EditorConfig セクションからの規則は、より近いファイルの規則が優先されるように、読み取られた順序で適用されます。

## <a name="supported-settings"></a>サポートされる設定

Visual Studio のエディターは、[EditorConfig プロパティ](http://editorconfig.org/#supported-properties)のコア セットから次をサポートします。

- indent_style
- indent_size
- tab_width
- end\_of_line
- 文字セット
- ルート

EditorConfig エディター設定は、XML を除き、Visual Studio 対応のすべての言語でサポートされています。 また、EditorConfig では、C# および Visual Basic の[コード スタイル](../ide/editorconfig-code-style-settings-reference.md)と[名前付け](../ide/editorconfig-naming-conventions.md)規則がサポートされます。

## <a name="editing-editorconfig-files"></a>EditorConfig ファイルの編集

Visual Studio では、.editorconfig ファイルを編集するための IntelliSense がいくつか提供されます。 たくさんの .editorconfig ファイルを編集する場合、[EditorConfig 言語サービス](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig)拡張機能が便利です。

EditorConfig ファイルを編集したら、コード ファイルを再度読み込んで新しい設定を有効にする必要があります。

## <a name="adding-and-removing-editorconfig-files"></a>EditorConfig ファイルの追加と削除

EditorConfig ファイルをプロジェクトまたはコードベースに追加しても既存のスタイルが新しいスタイルに変換されることはありません。 たとえば、タブで書式設定されているインデントがファイル内にあり、スペースでインデントする EditorConfig ファイルを追加する場合、インデント文字はスペースに変換されません。 ただし、新しいコード行はすべて、EditorConfig ファイルに従って書式設定されます。

EditorConfig ファイルをプロジェクトまたはコードベースから削除する場合は、開いているコード ファイルをすべて閉じてから再度開き、新しいコード行のグローバル エディター設定に戻す必要があります。

## <a name="example"></a>例

以下は、.editorconfig ファイルをプロジェクトに追加する前と追加した後の C# コード スニペットのインデント状態を示す例です。 Visual Studio テキスト エディターの **[オプション]** ダイアログ ボックスにある **[タブ]** 設定は、**Tab** キーを押したときに空白文字を入力するように設定されています。

![テキスト エディター タブの設定](../ide/media/vside_editorconfig_tabsetting.png)

設定どおり、次の行で **Tab** キーを押すと、4 つ分の空白文字が追加されてインデントが行われます。

![EditorConfig を使用する前のコード](../ide/media/vside_editorconfig_before.png)

.editorconfig という名前の新しいファイルを、次のコンテンツと共にプロジェクトに追加します。 `[*.cs]` 設定は、この変更がこのプロジェクトの C# コード ファイルにのみ適用されることを意味します。

```
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

これで、**Tab** キーを押すと、スペースの代わりにタブ文字が入力されます。

![Tab キーでタブ文字が追加されます](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshooting-editorconfig-settings"></a>EditorConfig 設定のトラブルシューティング

EditorConfig ファイルがディレクトリ構造内でプロジェクトの場所と同じか上位にある場合、Visual Studio はそのファイル内のエディター設定をエディターに適用します。 この場合、ステータス バーに次のメッセージが表示される場合があります。

   **"このファイルの種類のユーザー設定は、このプロジェクトのコーディング規則により上書きされます。"**

つまり、**[ツール]**、**[オプション]**、**[テキスト エディター]** の任意のエディター設定 (インデントのサイズとスタイル、タブ サイズ、コーディング規則など) が、ディレクトリ構造内でプロジェクトと同じか上位にある EditorConfig ファイルで指定されると、EditorConfig ファイル内の規則がオプションの設定よりも優先されます。 この動作は、**[ツール]**、**[オプション]**、**[テキスト エディター]** の **[プロジェクトのコーディング規則に従います]** オプションを切り替えることで制御できます。 このオプションをオフにすると、Visual Studio の EditorConfig に対するサポートが無効になります。

![[ツール] メニューの [オプション] - [プロジェクトのコーディング規則に従います]](media/coding_conventions_option.png)

親ディレクトリで任意の .editorconfig ファイルを見つけるには、コマンド プロンプトを開き、プロジェクトが格納されているディスクのルートから次のコマンドを実行します。

```
dir .editorconfig /s
```

EditorConfig 規則の範囲を制御するには、リポジトリのルートにある、またはプロジェクトが格納されているディレクトリ内の .editorconfig ファイルで ```root=true``` プロパティ を設定します。 Visual Studio は、開かれたファイルのディレクトリ内とすべての親ディレクトリで .editorconfig という名前のファイルを探します。 ルート ファイル パスに到達するか、```root=true``` の .editorconfig ファイルが見つかった場合、Visual Studio は検索を停止します。

## <a name="see-also"></a>関連項目

[.NET コード表記規則](../ide/editorconfig-code-style-settings-reference.md)  
[言語サービスの EditorConfig のサポート](../extensibility/supporting-editorconfig.md)  
[EditorConfig.org](http://editorconfig.org/)  
[コード エディターでのコードの作成](writing-code-in-the-code-and-text-editor.md)