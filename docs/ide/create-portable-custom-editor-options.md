---
title: "移植可能なカスタム エディター設定を作成する | Microsoft Docs"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 29
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 203e1e27cc892e96b103fc6cb22a73672a8e16af
ms.openlocfilehash: 70f3c6c7e4356a698aa6c1dd265f6c79c662673e
ms.lasthandoff: 03/01/2017

---
# <a name="create-portable-custom-editor-settings"></a>移植可能なカスタム エディター設定を作成する
Visual Studio のテキスト エディター設定は、指定された型のすべてのプロジェクトに適用されます。 そのため、たとえば、C# テキスト エディター設定を変更した場合、その設定は Visual Studio の*すべて*の C# プロジェクトに適用されます。 ただし、自分の好みのエディター設定とは異なる規則を使用しなければならないこともあります。 これを可能にするのが [EditorConfig](http://editorconfig.org/) ファイルであり、プロジェクトごとに一般的なテキスト エディターのオプションを指定することができます。 コードベースに追加された .editorconfig ファイルに含まれる EditorConfig 設定は、グローバルな Visual Studio テキスト エディター設定より優先されます。 つまり、自分の好みのテキスト エディター設定を使用するように各コードベースを調整できます。 Visual Studio でこの機能を使用するためのプラグインは必要ありません。

## <a name="coding-consistency"></a>コーディングの一貫性
EditorConfig ファイルの設定を利用すれば、使用するエディターや IDE に関係なく、コードベースで、ある言語に対して、コーディングのスタイルと設定に一貫性を維持できます。たとえば、インデントのスタイル、タブの幅、行末文字、エンコードなどです。 たとえば、C# でコーディングするとき、インデントを常に&5; つ分の空白文字で構成し、文書で UTF-8 エンコードを使用し、各行が常に CR/LF で終わるというという慣習をコードベースに与えるのであれば、そのように .editorconfig ファイルを構成できます。

個人的なプロジェクトで使用するコーディング規則は、チームのプロジェクトで使用するそれとは変えることができます。 たとえば、コーディングするとき、あなたは Tab キーを押して TAB 文字を追加することを好むかもしれません。 しかしながら、チームは、インデントで TAB 文字ではなく&4; つ分の空白文字を追加することを希望するかもしれません。 EditorConfig ファイルがこの問題を解決します。シナリオごとに構成を与えることができるからです。

設定はコードベースのファイルに含まれているため、そのコードベースと共に移動します。 EditorConfig 対応のエディターでコード ファイルを開く限り、テキスト エディター設定が実装されます。 EditorConfig ファイルの詳細については、[EditorConfig.org](http://editorconfig.org/) Web サイトをご覧ください。 たくさんの .editorconfig ファイルを編集する場合、[EditorConfig 言語サービス](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig)拡張機能が便利です。

## <a name="override-editorconfig-settings"></a>EditorConfig 設定を上書きする
ファイル階層のフォルダーに .editorconfig ファイルを追加すると、その設定がその階層レベルとその下のレベルのあらゆる該当ファイルに適用されます。 特定のプロジェクトまたはコードベースの EditorConfig 設定を上書きし、最上位の .editorconfig ファイルとは異なる (優先する) 値を使用するには、変更するレベルに .editorconfig ファイルを追加します。

![EditorConfig 階層](../ide/media/vside_editorconfig_hierarchy.png)

新しい .editorconfig ファイル設定は、そのファイルが置かれているレベルとすべての下位ファイルに適用されます。

## <a name="supported-settings"></a>サポートされる設定
Visual Studio のエディターは、EditorConfig オプションのコア セットの次の値をサポートしています。
- indent_style
- indent_size
- tab_width
- end_of_line
- 文字セット
- ルート
- [コード表記規則](../ide/editorconfig-code-style-settings-reference.md)

EditorConfig 設定は、XML を除き、Visual Studio 対応のすべての言語で利用できます。

## <a name="example"></a>例
これは C# コード スニペットのインデント状態を示すサンプルです。.editorconfig ファイルをプロジェクトに追加する前と追加した後を確認できます。 Visual Studio テキスト エディターの **[オプション]** ダイアログ ボックスにある **[タブ]** 設定は、コード内で TAB キーを押したときに空白文字を入力するように設定されています。

![テキスト エディター タブの設定](../ide/media/vside_editorconfig_tabsetting.png)

設定どおり、次の行で TAB キーを押すと、4 つ分の空白文字が追加されてインデントが行われます。

![EditorConfig を使用する前のコード](../ide/media/vside_editorconfig_before.png)

.editorconfig という名前の新しいファイルをプロジェクトに追加します。 (`[*.cs]` 設定は、この変更がこのプロジェクトの .cs ファイルにのみ適用されることを意味します。)

![プロジェクトへの .editorconfig ファイルの追加](../ide/media/vside_editorconfig_addconfig.png)

これで、TAB キーを押すと、スペースの代わりにタブ文字が入力されます。

![TAB で Tab 文字が追加されます](../ide/media/vside_editorconfig_tab.png)

> [!NOTE]
>  .editorconfig ファイルをプロジェクトまたはコードベースに追加しても既存のスタイルが新しいスタイルに変換されることはありません。新しく追加した行にのみ適用されます。 プロジェクトまたはコードベースから .editorconfig ファイルを削除する場合、エディター設定のコード ファイルを再読み込みし、グローバル設定に戻す必要があります。 .editorconfig ファイルに間違いがある場合、Visual Studio の [エラー] ウィンドウに表示されます。

## <a name="support-editorconfig-for-your-language-service"></a>言語サービスの EditorConfig のサポート

ほとんどの場合、Visual Studio 言語サービスを実装するとき、EditorConfig ユニバーサル プロパティをサポートするための追加の作業は必要ありません。 ユーザーがファイルを開くと、コア エディターが .editorconfig ファイルを自動的に検出して読み込み、適切なテキスト バッファーとビュー オプションを設定します。 ただし、一部の言語サービスでは、ユーザーがテキストを編集または書式設定するとき、タブやスペースなどのアイテムにグローバル設定を使用せず、コンテキストに基づいてテキスト ビュー オプションが使用されます。 そのような場合は、EditorConfig ファイルをサポートするように言語サービスを更新する必要があります。

次の表は、EditorConfig ファイルをサポートするように言語サービスを更新するために必要な変更をまとめたものです。

| 使用されていないグローバル言語固有オプション | コンテキストに基づくオプションの変更 |
| :------------- | :------------- |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs または Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs | !textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId) または !textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId) |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize または Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize | textBufferOptions.GetOptionValue(DefaultOptions. IndentSizeOptionId) または textView.Options.GetOptionValue(DefaultOptions. IndentSizeOptionId) |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize または Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize | textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId) または textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId) |

