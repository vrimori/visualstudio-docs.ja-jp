---
title: "EditorConfig で移植可能なカスタム エディター設定を作成する | Microsoft Docs"
ms.custom: 
ms.date: 10/27/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editor
ms.assetid: 
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-general
ms.openlocfilehash: 2c1df6f8e34d2b8e72486dd804ba57f0dcf2406b
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2017
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>EditorConfig で移植可能なカスタム エディター設定を作成する
Visual Studio のテキスト エディター設定は、指定された型のすべてのプロジェクトに適用されます。 そのため、たとえば、C# テキスト エディター設定を変更した場合、その設定は Visual Studio の*すべて*の C# プロジェクトに適用されます。 ただし、自分の好みのエディター設定とは異なる規則を使用しなければならないこともあります。 これを可能にするのが [EditorConfig](http://editorconfig.org/) ファイルであり、プロジェクトごとに一般的なテキスト エディターのオプションを指定することができます。 コードベースに追加された .editorconfig ファイルに含まれる EditorConfig 設定は、グローバルな Visual Studio テキスト エディター設定より優先されます。 つまり、自分の好みのテキスト エディター設定を使用するように各コードベースを調整できます。 Visual Studio でこの機能を使用するためのプラグインは必要ありません。

## <a name="coding-consistency"></a>コーディングの一貫性
EditorConfig ファイルの設定を利用すれば、使用するエディターや IDE に関係なく、コードベースで、ある言語に対して、コーディングのスタイルと設定に一貫性を維持できます。たとえば、インデントのスタイル、タブの幅、行末文字、エンコードなどです。 たとえば、C# でコーディングするとき、インデントを常に 5 つ分の空白文字で構成し、文書で UTF-8 エンコードを使用し、各行が常に CR/LF で終わるというという慣習をコードベースに与えるのであれば、そのように .editorconfig ファイルを構成できます。

個人的なプロジェクトで使用するコーディング規則は、チームのプロジェクトで使用するそれとは変えることができます。 たとえば、コーディングするとき、あなたは Tab キーを押して TAB 文字を追加することを好むかもしれません。 しかしながら、チームは、インデントで TAB 文字ではなく 4 つ分の空白文字を追加することを希望するかもしれません。 EditorConfig ファイルがこの問題を解決します。シナリオごとに構成を与えることができるからです。

設定はコードベースのファイルに含まれているため、そのコードベースと共に移動します。 EditorConfig 対応のエディターでコード ファイルを開く限り、テキスト エディター設定が実装されます。 EditorConfig ファイルの詳細については、[EditorConfig.org](http://editorconfig.org/) Web サイトをご覧ください。

## <a name="override-editorconfig-settings"></a>EditorConfig 設定を上書きする
ファイル階層のフォルダーに .editorconfig ファイルを追加すると、その設定がその階層レベルとその下のレベルのあらゆる該当ファイルに適用されます。 特定のプロジェクトまたは codebase が最上位の .editorconfig ファイルとは異なる規則を使用するように、それらの EditorConfig 設定を上書きするには、codebase のリポジトリまたはプロジェクト ディレクトリのルートに .editorconfig ファイルを追加します。 Visual Studio がそのディレクトリ構造より上にある .editorconfig ファイルを検索しないように、ファイルに ```root=true``` プロパティを必ず配置します。 新しい .editorconfig ファイル設定は、そのファイルが置かれているレベルと任意のサブディレクトリ内のファイルに適用されます。

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
- end_of_line
- 文字セット
- ルート

さらに、[.NET コード スタイル規則](../ide/editorconfig-code-style-settings-reference.md)をサポートします。  

EditorConfig 設定は、XML を除き、Visual Studio 対応のすべての言語で利用できます。

## <a name="intellisense"></a>IntelliSense
Visual Studio では、.editorconfig ファイルを編集するための制限付きの IntelliSense を提供しています。 たくさんの .editorconfig ファイルを編集する場合、[EditorConfig 言語サービス](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig)拡張機能が便利です。

## <a name="example"></a>例
これは C# コード スニペットのインデント状態を示すサンプルです、.editorconfig ファイルをプロジェクトに追加する前と追加した後を確認できます。 Visual Studio テキスト エディターの **[オプション]** ダイアログ ボックスにある **[タブ]** 設定は、コード内で **Tab** キーを押したときに空白文字を入力するように設定されています。

![テキスト エディター タブの設定](../ide/media/vside_editorconfig_tabsetting.png)

設定どおり、次の行で **Tab** キーを押すと、4 つ分の空白文字が追加されてインデントが行われます。

![EditorConfig を使用する前のコード](../ide/media/vside_editorconfig_before.png)

.editorconfig という名前の新しいファイルを、次のコンテンツと共にプロジェクトに追加します。 `[*.cs]` 設定は、この変更がこのプロジェクトの .cs ファイルにのみ適用されることを意味します。  

![プロジェクトへの .editorconfig ファイルの追加](../ide/media/vside_editorconfig_addconfig.png)

これで、**Tab** キーを押すと、スペースの代わりにタブ文字が入力されます。

![TAB で Tab 文字が追加されます](../ide/media/vside_editorconfig_tab.png)

> [!NOTE]
>  .editorconfig ファイルをプロジェクトまたはコードベースに追加しても既存のスタイルが新しいスタイルに変換されることはありません。新しく追加した行にのみ適用されます。 プロジェクトまたはコードベースから .editorconfig ファイルを削除する場合、エディター設定のコード ファイルを再読み込みし、グローバル設定に戻す必要があります。 .editorconfig ファイルに間違いがある場合、Visual Studio の [エラー一覧] ウィンドウに表示されます。

## <a name="troubleshooting-editorconfig-settings"></a>EditorConfig 設定のトラブルシューティング
EditorConfig ファイルがディレクトリ構造内でプロジェクトの場所と同じか上位にある場合、Visual Studio はそのファイル内のエディター設定をエディターに適用します。 この場合、ステータス バーに次のメッセージが表示される場合があります。

**"このファイルの種類のユーザー設定は、このプロジェクトのコーディング規則により上書きされます。"**

つまり、**[ツール]**、**[オプション]**、**[テキスト エディター]** の任意のエディターの設定 (インデント サイズ、タブ サイズ、インデント スタイル &mdash; タブまたはスペース、または `var` の使用などのコーディング規則など) が、ディレクトリ構造内でプロジェクトと同じか上位にある EditorConfig ファイルで指定されると、EditorConfig ファイル内の規則がオプションの設定よりも優先されます。 この動作は、**[ツール]**、**[オプション]**、**[テキスト エディター]** の **[プロジェクトのコーディング規則に従います]** オプションを切り替えることで制御できます。 このオプションをオフにすると、Visual Studio の EditorConfig に対するサポートが無効になります。

![[ツール] メニューの [オプション] - [プロジェクトのコーディング規則に従います]](media/coding_conventions_option.png)

親ディレクトリで .editorconfig ファイルを見つけるには、コマンド プロンプトを開き、プロジェクトが格納されているディスクのルートから次のコマンドを実行します。

```
dir .editorconfig /s
```

EditorConfig 規則の範囲を制御するには、リポジトリのルートにある、またはプロジェクトが格納されているディレクトリ内の .editorconfig ファイルで ```root=true``` プロパティ を設定します。 Visual Studio は、開かれたファイルのディレクトリ内とすべての親ディレクトリで .editorconfig という名前のファイルを探します。 ルート ファイル パスに到達するか、```root=true``` の .editorconfig ファイルが見つかった場合、Visual Studio は検索を中止します。

## <a name="support-editorconfig-for-your-language-service"></a>言語サービスの EditorConfig のサポート
ほとんどの場合、Visual Studio 言語サービスを実装するとき、EditorConfig ユニバーサル プロパティをサポートするための追加の作業は必要ありません。 ユーザーがファイルを開くと、コア エディターが .editorconfig ファイルを自動的に検出して読み込み、適切なテキスト バッファーとビュー オプションを設定します。 ただし、一部の言語サービスでは、ユーザーがテキストを編集または書式設定するとき、タブやスペースなどのアイテムにグローバル設定を使用せず、コンテキストに基づいてテキスト ビュー オプションが使用されます。 そのような場合は、EditorConfig ファイルをサポートするように言語サービスを更新する必要があります。

以下は、グローバルの_言語固有_オプションを_コンテキスト_ オプションに置き換えることで、言語サービスを更新して EditorConfig ファイルをサポートするために必要な変更です。  

### <a name="indent-style"></a>インデント スタイル
置換:  

Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs  
_または_  
Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs  

代入:  

!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)  
_または_  
!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)  

### <a name="indent-size"></a>[インデント サイズ]
置換:  

Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize  
_または_  
Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize  

代入:  

textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)  
_または_  
textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)  

### <a name="tab-size"></a>[タブ サイズ]
置換:  

Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize  
_または_  
Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize  

代入:  

textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)  
_または_  
textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)  

## <a name="see-also"></a>関連項目
[.NET コード表記規則](../ide/editorconfig-code-style-settings-reference.md)  
[EditorConfig.org](http://editorconfig.org/)  
[コード エディターでのコードの作成](writing-code-in-the-code-and-text-editor.md)