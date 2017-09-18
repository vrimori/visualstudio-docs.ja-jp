---
title: "チュートリアル: 余白のグリフの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "新たな利益のグリフのエディター [Visual Studio SDK]"
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# チュートリアル: 余白のグリフの作成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

エディターのマージンの外観をカスタマイズするには、カスタム エディター拡張機能を使用します。 このチュートリアルは、コードのコメント内"todo という"単語が出現するたびに、インジケーター マージンにカスタム グリフを設定します。  
  
## 必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
## MEF プロジェクトを作成します。  
  
1.  C\# の場合は、VSIX プロジェクトを作成します。 \(で、 **新しいプロジェクト** ダイアログで、 **Visual c\#\/機能拡張**, 、し **VSIX プロジェクト**.\) ソリューションの名前 `TodoGlyphTest`します。  
  
2.  エディターの分類子プロジェクト項目を追加します。 詳細については、「[エディター項目テンプレートを使用して拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)」を参照してください。  
  
3.  既存のクラス ファイルを削除します。  
  
## グリフを定義します。  
 実装することによって、グリフを定義、 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> インターフェイスです。  
  
#### グリフを定義するには  
  
1.  クラス ファイルを追加し、名前 `TodoGlyphFactory`します。  
  
2.  次の追加の宣言を使用します。  
  
     [!code-cs[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  という名前のクラスを追加 `TodoGlyphFactory` を実装する <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>です。  
  
     [!code-cs[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  グリフのディメンションを定義するプライベート フィールドを追加します。  
  
     [!code-cs[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  実装 `GenerateGlyph` グリフのユーザー インターフェイス \(UI\) 要素を定義しています。`TodoTag` このチュートリアルで後で定義されます。  
  
     [!code-cs[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  という名前のクラスを追加 `TodoGlyphFactoryProvider` を実装する <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>です。 このクラスをエクスポート、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph"の <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> 後 VsTextMarker の <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "code"の <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag のです。  
  
     [!code-cs[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  実装、 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> メソッドをインスタンス化して、 `TodoGlyphFactory`です。  
  
     [!code-cs[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## Todo タグとタガーを定義します。  
 前の手順で定義されている UI 要素とインジケーター マージン間のリレーションシップを定義するには、タグの種類とタガーを作成し、タガー プロバイダーを使用してエクスポートします。  
  
#### Todo タグとタガーを定義するには  
  
1.  新しいクラス ファイルをプロジェクトに追加し、名前 `TodoTagger`します。  
  
2.  次の imports を追加します。  
  
     [!code-cs[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  という名前のクラスを追加 `TodoTag`します。  
  
     [!code-cs[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  という名前のクラスを変更して `TodoTagger` を実装する <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 型の `TodoTag`です。  
  
     [!code-cs[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  `TodoTagger` クラスのプライベート フィールドを追加、 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> の分類内を検索するテキストにまたがっている場合。  
  
     [!code-cs[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  分類子を設定するコンス トラクターを追加します。  
  
     [!code-cs[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  実装、 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> すべての分類を検索して特定のメソッドにわたる名前は「コメント」という語を含むし、テキストには、検索テキストが含まれています。 検索テキストが見つかったときに、新しい yield 戻る <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> 型の `TodoTag`です。  
  
     [!code-cs[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  宣言、 `TagsChanged` イベントです。  
  
     [!code-cs[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. という名前のクラスを追加 `TodoTaggerProvider` を実装する <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, 、およびエクスポートして、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "code"の <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag のです。  
  
     [!code-cs[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. インポート、 <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>です。  
  
     [!code-cs[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. 実装、 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> メソッドをインスタンス化して、 `TodoTagger`です。  
  
     [!code-cs[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## コードのビルドとテスト  
 このコードをテストするには、TodoGlyphTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### ビルドし、TodoGlyphTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  F5 キーを押して、プロジェクトを実行します。 Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
3.  インジケーター マージンが表示されていることを確認します。 \(上、 **ツール** \] メニューのをクリックして **オプション**します。**テキスト エディター** ことを確認\] ページで、 **インジケーター マージン** が選択されている\)。  
  
4.  コメントのあるコード ファイルを開きます。 コメントのセクションでは、のいずれかに"todo"という単語を追加します。  
  
5.  濃い青のアウトラインを持つ、明るい青色の円は、コード ウィンドウの左側にあるインジケーター マージンに表示されます。