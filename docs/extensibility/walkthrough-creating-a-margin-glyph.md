---
title: 'チュートリアル: 余白グリフを作成する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 811985ef45fb43b08b771f2bc417a512c290726c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-margin-glyph"></a>チュートリアル: 余白グリフを作成します。
カスタム エディターの拡張機能を使用して、エディターのマージンの外観をカスタマイズできます。 このチュートリアルは、"todo"という単語がコード コメント内に表示されるたびに、インジケーター マージンにカスタム グリフを格納します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-mef-project"></a>MEF プロジェクトを作成します。  
  
1.  C# の場合は、VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューションの名前を付けます`TodoGlyphTest`です。  
  
2.  エディター分類子プロジェクト項目を追加します。 詳細については、次を参照してください。[エディター項目テンプレートに、拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)です。  
  
3.  既存のクラス ファイルを削除します。  
  
## <a name="defining-the-glyph"></a>グリフを定義します。  
 実装することで、グリフを定義、<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>インターフェイスです。  
  
#### <a name="to-define-the-glyph"></a>グリフを定義するには  
  
1.  クラス ファイルを追加し、名前を付けます`TodoGlyphFactory`です。  
  
2.  次の追加の宣言を使用します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  という名前のクラスを追加`TodoGlyphFactory`を実装する<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>です。  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  グリフのディメンションを定義するプライベート フィールドを追加します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  実装`GenerateGlyph`グリフのユーザー インターフェイス (UI) 要素を定義します。 `TodoTag` このチュートリアルの後半で定義されます。  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  という名前のクラスを追加`TodoGlyphFactoryProvider`を実装する<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>です。 このクラスをエクスポート、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph"の<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>後 VsTextMarker の<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"code"のおよび<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>TodoTag のです。  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  実装、<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A>をインスタンス化することによって、`TodoGlyphFactory`です。  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Todo タグとタガーを定義します。  
 前の手順で定義されている UI 要素と、インジケーター マージン間のリレーションシップを定義するには、タグの種類と、タガーを作成し、タガー プロバイダーを使用してエクスポートします。  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>Todo のタグおよびタガーを定義するには  
  
1.  新しいクラス ファイルをプロジェクトに追加し、名前`TodoTagger`です。  
  
2.  次の imports を追加します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  という名前のクラスを追加`TodoTag`です。  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  という名前のクラスを変更`TodoTagger`を実装する<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>型の`TodoTag`します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  `TodoTagger`クラスのプライベート フィールドを追加、<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>の分類内を検索するテキストにまたがるとします。  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  分類子を設定するコンス トラクターを追加します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  実装、<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>によってすべての分類を検索するメソッドにわたる名前は「コメント」という単語を含めるし、テキストが検索文字列が含まれています。 検索テキストが見つかったときに、新しい yield 戻る<xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>型の`TodoTag`します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  宣言、`TagsChanged`イベント。  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. という名前のクラスを追加`TodoTaggerProvider`を実装する<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>、およびエクスポートして、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "code"のおよび<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>TodoTag のです。  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. インポート、<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>です。  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. 実装、<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>をインスタンス化することによって、`TodoTagger`です。  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
 このコードをテストするには、TodoGlyphTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>ビルドし、TodoGlyphTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  F5 キーを押してプロジェクトを実行します。 Visual Studio の 2 番目のインスタンスがインスタンス化されます。  
  
3.  インジケーター マージンが表示されていることを確認します。 (上、**ツール** メニューのをクリックして**オプション**です。 **テキスト エディター**ことを確認 ページで、**インジケーター マージン**が選択されている)。  
  
4.  コメントのあるコード ファイルを開きます。 コメントのセクションでは、のいずれかに、"todo"という単語を追加します。  
  
5.  濃い青アウトラインを持つ明るい青色は、コード ウィンドウの左側に、インジケーター マージンに表示されます。