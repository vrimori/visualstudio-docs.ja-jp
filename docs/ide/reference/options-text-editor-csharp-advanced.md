---
title: "[オプション]、[テキスト エディター]、[C#]、[詳細] | Microsoft Docs"
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- XML documentation, creating
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 5d6cf8b655151e9b07111b6ac6fd64b6ad3c845f
ms.sourcegitcommit: 238cd48787391aa0ed1eb684f3f04e80f7958705
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="options-text-editor-c-advanced"></a>[オプション]、[テキスト エディター]、[C#]、[詳細]

**[詳細]** オプションを使って、C# のエディターの書式設定、コードのリファクタリング、および XML ドキュメントのコメントの設定を変更します。 このオプション ページにアクセスするには、**[ツール]** > **[オプション]** を選び、さらに **[テキスト エディター]** > **[C#]** > **[詳細]** の順に選びます。

> [!NOTE]
> 実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)」を参照してください。

## <a name="analysis"></a>分析

- 完全ソリューション解析を有効にする

   開いているコード ファイルだけでなく、ソリューションのすべてのファイルでコード分析を有効にします。 詳細については、[完全ソリューション解析](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)に関するページを参照してください。

- 外部プロセスでエディター機能解析を実行する (試験段階)

## <a name="using-directives"></a>Using ディレクティブ

- using を並べ替える際に、'System' ディレクティブを先頭に配置する

- ディレクティブ グループを使用して分離します

- 参照アセンブリの型に using を提案する

- NuGet パッケージの型に using を提案する

## <a name="highlighting"></a>強調表示

- カーソルの下にあるシンボルへの参照をハイライトする

   シンボル内にカーソルを置いたり、シンボルをクリックしたりすると、コード ファイル内のそのシンボルのすべてのインスタンスが強調表示されます。

- カーソルの下にあるキーワードの関連キーワードをハイライトする

## <a name="outlining"></a>アウトライン

- ファイルが開かれたときにアウトライン モードを実行する

   選択すると、コードの折りたたみ可能なブロックを作成するコード ファイルが自動的にアウトラインになります。 初めてファイルが開かれると、#regions ブロックとアクティブでないコード ブロックが折りたたまれます。

- プロシージャ行の区切り記号を表示する

- 宣言レベルのコンストラクトのアウトラインを表示する

- コード レベルのコンストラクトのアウトラインを表示する

- コメントとプリプロセッサ領域のアウトラインを表示する

- 定義を折りたたむときに #regions を折りたたむ

## <a name="fading"></a>フェード

- 未使用の using をフェードアウトします

- 到達できないコードをフェードアウトします

## <a name="block-structure-guides"></a>ブロック構造のガイド

- 宣言レベルのコンストラクトのガイドを表示する

- コード レベルのコンストラクトのガイドを表示する

## <a name="editor-help"></a>エディターのヘルプ

- /// が入力されたとき、XML ドキュメントのコメントを生成する

   オンにすると、`///` コメント イントロダクションを入力した後に、XML ドキュメント コメントの XML 要素が挿入されます。 XML ドキュメントの詳細については、「[XXML ドキュメント コメント (C# プログラミング ガイド)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)」を参照してください。

- /\* \*/ コメントを記述する際、新しい行の先頭に \* を挿入する

- 名前変更追跡のプレビューの表示

- Enter で文字列リテラルを分割する

- 'string.Format' 呼び出しの無効なプレースホルダーをレポートします

## <a name="extract-method"></a>メソッドの抽出

- カスタム構造体に ref または out を設定しない

## <a name="implement-interface-or-abstract-class"></a>インターフェイスまたは抽象クラスの実装

- [プロパティ、イベント、メソッドを挿入する際には、次の場所に挿入します]: [同じ種類の他のメンバーと共に] または [at the end]\(末尾\)

- [プロパティの生成時]: [スロー プロパティを優先する] または [自動プロパティを優先する]

## <a name="see-also"></a>関連項目

[方法: ドキュメント生成のための XML コメントを挿入する](../../ide/reference/generate-xml-documentation-comments.md)  
[XML ドキュメント コメント (C# プログラミング ガイド)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)  
[XML コメントによるコードの文書化 (C# ガイド)](/dotnet/csharp/codedoc)  
[言語固有のエディター オプションの設定](../../ide/reference/setting-language-specific-editor-options.md)  
[C# IntelliSense](../../ide/visual-csharp-intellisense.md)