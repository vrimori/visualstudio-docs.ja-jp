---
title: '方法 : LinqToXmlDataBinding という例をビルドして実行する'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1164312d74259ad4f3a56750a487fb2578595cf0
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924162"
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>方法: LinqToXmlDataBinding という例をビルドして実行する

このトピックでは、LinqToXmlDataBinding という Visual Studio プロジェクトを作成してビルドする方法、および結果として生成される LinqToXmlDataBinding という Windows Presentation Foundation (WPF) プログラムの例を実行する方法について説明します。

Visual Studio の詳細については、「[Visual Studio IDE の概要](../ide/visual-studio-ide.md)」を参照してください。

## <a name="create-and-populate-the-project"></a>プロジェクトの作成および設定

### <a name="to-create-the-starting-project"></a>基本となるプロジェクトを作成するには

1. Visual Studio を起動し、LinqToXmlDataBinding という名前の C# WPF アプリケーションを作成します。 プロジェクトでは、.NET Framework 3.5 (またはそれ以降) を使用する必要があります。

1. 次の .NET アセンブリ用のプロジェクト参照がない場合は追加します。

    - System.Data

    - System.Data.DataSetExtensions

    - System.Xml

    - System.Xml.Linq

1. **Ctrl** キーと **Shift** キーを押しながら **B** キーを押してソリューションをビルドし、**F5** キーを押してそのソリューションを実行します。 プロジェクトがエラーなくコンパイルされ、汎用 WPF アプリケーションとして実行されます。

### <a name="to-add-custom-code-to-the-project"></a>プロジェクトにカスタム コードを追加するには

1. ソリューション エクスプローラーでソース ファイル **Window1.xaml** の名前を **L2XDBForm.xaml** に変更します。 依存するソース ファイル **Window1.xaml.cs** の名前が、自動的に **L2XDBForm.xaml.cs** に変更されます。

1. ファイル **L2XDBForm.xaml** 内のソース コードを、トピック「[L2DBForm.xaml ソース コード](../designers/l2dbform-xaml-source-code.md)」のコードで置き換えます。 このファイルは XAML ソース ビューで操作します。

1. 同様に、**L2XDBForm.xaml.cs** 内のソースを「[L2DBForm.xaml.cs ソース コード](../designers/l2dbform-xaml-cs-source-code.md)」のコードで置き換えます。

1. ファイル **App.xaml** で、文字列 `Window1.xaml` をすべて `L2XDBForm.xaml` で置き換えます。

1. **Ctrl** キーと **Shift** キーを押しながら **B** キーを押して、ソリューションをビルドします。

## <a name="run-the-program"></a>プログラムを実行する

LinqToXmlDataBinding プログラムを使用すると、ユーザーは、組み込まれた XML 要素として格納されている書籍一覧を表示したり、操作したりできるようになります。

### <a name="to-run-the-program-and-view-the-book-list"></a>プログラムを実行して書籍一覧を表示するには

- **F5** キー (**[デバッグ開始]**) または **Ctrl** キーを押しながら **F5** キー (**[デバッグなしで開始]**) を押して、LinqToXmlDataBinding を実行します。

   **[WPF Data Binding using LINQ to XML]** というタイトルのプログラム ウィンドウが表示されます。

- UI の最上部に、書籍一覧を表す生の **XML** が表示されます。 この部分は WPF の <xref:System.Windows.Controls.TextBlock> コントロールを使って表示されており、マウスやキーボードで操作できません。

- **[Book List]** というラベルの付いた 2 番目のセクションには、プレーンテキストの順序付けられた一覧として書籍が表示されます。 この部分では <xref:System.Windows.Controls.ListBox> コントロールが使用されており、マウスまたはキーボードによる選択が可能です。

### <a name="to-add-and-delete-books-from-the-list"></a>一覧に対して書籍を追加および削除するには

- 一覧に新しい書籍を追加するには、最後のセクションである **[Add New Book]** にある **[ID]** および **[Value]** の <xref:System.Windows.Controls.TextBox> コントロールに値を入力し、**[Add Book]** ボタンをクリックします。 書籍一覧と XML の両方に書籍が追加されます。 このプログラムでは入力値が検証されません。

- 一覧から既存の書籍を削除するには、**[Book List]** セクションで書籍を選択し、**[Remove Selected Book]** ボタンをクリックします。 書籍一覧および生の XML ソースの両方で書籍のエントリが削除されます。

### <a name="to-edit-an-existing-book-entry"></a>既存の書籍エントリを編集するには

1. 2 番目の **[Book List]** セクションで書籍エントリを選択します。 3 番目のセクションである **[Edit Selected Book]** に現在の値が表示されます。

1. キーボードを使用して値を編集します。 いずれかの <xref:System.Windows.Controls.TextBox> コントロールがフォーカスを失った時点で、XML ソースと書籍一覧の両方に変更が自動的に反映されます。

## <a name="see-also"></a>関連項目

- [LINQ to XML を使用した WPF のデータ バインディングの例](../designers/wpf-data-binding-using-linq-to-xml-example.md)
- [チュートリアル : LinqToXmlDataBinding の例](../designers/walkthrough-linqtoxmldatabinding-example.md)
- [Visual Studio IDE の概要](../ide/visual-studio-ide.md)