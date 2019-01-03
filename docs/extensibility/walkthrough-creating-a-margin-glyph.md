---
title: 'チュートリアル: 余白のグリフの作成 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce1d3449c786211c90df52b0633c84cf2a491769
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53851353"
---
# <a name="walkthrough-create-a-margin-glyph"></a>チュートリアル: 余白のグリフを作成します。
エディターの余白の外観をカスタマイズするには、カスタム エディター拡張機能を使用します。 このチュートリアルは、"todo"という単語がコード コメント内に表示されるたびに、インジケーター マージンにカスタム グリフを設定します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールしないでください。 Visual Studio のセットアップのオプション機能として含まれています。 また、後から VS SDK をインストールすることもできます。 詳細については、"[Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)"を参照してください。  
  
## <a name="create-a-mef-project"></a>MEF プロジェクトを作成します。  
  
1.  C# VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログ ボックスで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューション `TodoGlyphTest`の名前を指定します。  
  
2.  エディター分類子プロジェクト項目を追加します。 詳細については、次を参照してください。[エディターの項目テンプレートを使用した拡張機能を作成する](../extensibility/creating-an-extension-with-an-editor-item-template.md)します。  
  
3.  既存のクラス ファイルを削除します。  
  
## <a name="define-the-glyph"></a>グリフを定義します。  
 実行して、グリフを定義、<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>インターフェイス。  
  
### <a name="to-define-the-glyph"></a>グリフを定義するには  
  
1.  クラス ファイルを追加し、その名前を `TodoGlyphFactory`にします。  
  
2.  宣言を使用して、次のコードを追加します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  という名前のクラスを追加`TodoGlyphFactory`を実装する<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  グリフの大きさを定義するプライベート フィールドを追加します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  実装`GenerateGlyph`グリフのユーザー インターフェイス (UI) 要素を定義します。 `TodoTag` このチュートリアルの後半で定義されます。  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  という名前のクラスを追加`TodoGlyphFactoryProvider`を実装する<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>します。 このクラスをエクスポート、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph"の<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>後 VsTextMarker の<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"code"の<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>TodoTag の。  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  実装、<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A>メソッドをインスタンス化して、`TodoGlyphFactory`します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## <a name="define-a-todo-tag-and-tagger"></a>Todo のタグとタガーを定義します。  
 前の手順で定義されている UI 要素と、インジケーター マージン間のリレーションシップを定義します。 タグの種類とタガーを作成し、タガー プロバイダーを使用してエクスポートします。  
  
### <a name="to-define-a-todo-tag-and-tagger"></a>Todo のタグとタガーを定義するには  
  
1.  新しいクラス ファイルをプロジェクトに追加し、名前`TodoTagger`します。  
  
2.  次の imports を追加します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  という名前のクラスを追加`TodoTag`します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  という名前のクラスを変更`TodoTagger`を実装する<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>型の`TodoTag`します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  `TodoTagger`クラスのプライベート フィールドを追加、<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>して、分類内で検索するテキストにまたがっています。  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  分類子を設定するコンス トラクターを追加します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  実装、<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>すべての分類を検索して特定のメソッドにわたる名前は「コメント」という単語を含めるし、テキストが検索テキストが含まれています。 検索テキストが見つかったときに、新しい yield 戻る<xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>型の`TodoTag`します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  宣言を`TagsChanged`イベント。  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. という名前のクラスを追加`TodoTaggerProvider`を実装する<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>、およびエクスポートして、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "code"の<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>TodoTag の。  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. インポート、<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. 実装、<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>メソッドをインスタンス化して、`TodoTagger`します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## <a name="build-and-test-the-code"></a>ビルドし、コードのテスト  
 このコードをテストするには、TodoGlyphTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
### <a name="to-build-and-test-the-todoglyphtest-solution"></a>ビルドして TodoGlyphTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  キーを押してプロジェクトを実行**F5**します。 Visual Studio の 2 番目のインスタンスを開始します。  
  
3.  インジケーター マージンが表示されていることを確認します。 (上、**ツール** メニューのをクリックして**オプション**します。 **テキスト エディター**ことを確認します ページで、**インジケーター マージン**が選択されている)。  
  
4.  コメントのあるコード ファイルを開きます。 コメントのセクションでは、のいずれかに"todo"という単語を追加します。  
  
5.  コード ウィンドウの左側に、インジケーター マージンに濃い青色の輪郭を明るい青色の円が表示されます。