---
title: 'チュートリアル: 余白のグリフの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 172ac543f8777219bb7c5adc94d19e1baeea24e7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783208"
---
# <a name="walkthrough-creating-a-margin-glyph"></a>チュートリアル: 余白のグリフの作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

エディターの余白の外観をカスタマイズするには、カスタム エディター拡張機能を使用します。 このチュートリアルは、"todo"という単語がコード コメント内に表示されるたびに、インジケーター マージンにカスタム グリフを設定します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-mef-project"></a>MEF プロジェクトを作成します。  
  
1.  C# VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログ ボックスで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューション `TodoGlyphTest`の名前を指定します。  
  
2.  エディター分類子プロジェクト項目を追加します。 詳細については、次を参照してください。[エディターの項目テンプレートを使用した拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)です。  
  
3.  既存のクラス ファイルを削除します。  
  
## <a name="defining-the-glyph"></a>グリフを定義します。  
 実装することで、グリフを定義、<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>インターフェイス。  
  
#### <a name="to-define-the-glyph"></a>グリフを定義するには  
  
1.  クラス ファイルを追加し、その名前を `TodoGlyphFactory`にします。  
  
2.  次の追加の宣言を使用します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#1)]
     [!code-vb[VSSDKTodoGlyphTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#1)]  
  
3.  という名前のクラスを追加`TodoGlyphFactory`を実装する<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#2)]
     [!code-vb[VSSDKTodoGlyphTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#2)]  
  
4.  グリフの大きさを定義するプライベート フィールドを追加します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#3)]
     [!code-vb[VSSDKTodoGlyphTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#3)]  
  
5.  実装`GenerateGlyph`グリフのユーザー インターフェイス (UI) 要素を定義します。 `TodoTag` このチュートリアルの後半で定義されます。  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#4)]
     [!code-vb[VSSDKTodoGlyphTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#4)]  
  
6.  という名前のクラスを追加`TodoGlyphFactoryProvider`を実装する<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>します。 このクラスをエクスポート、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph"の<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>後 VsTextMarker の<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"code"の<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>TodoTag の。  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#5)]
     [!code-vb[VSSDKTodoGlyphTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#5)]  
  
7.  実装、<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A>メソッドをインスタンス化して、`TodoGlyphFactory`します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#6)]
     [!code-vb[VSSDKTodoGlyphTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#6)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Todo のタグとタガーを定義します。  
 前の手順で定義されている UI 要素と、インジケーター マージン間のリレーションシップを定義するには、タグの種類と、タガーを作成し、タガー プロバイダーを使用してエクスポートします。  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>Todo のタグとタガーを定義するには  
  
1.  新しいクラス ファイルをプロジェクトに追加し、名前`TodoTagger`します。  
  
2.  次の imports を追加します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#7)]
     [!code-vb[VSSDKTodoGlyphTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#7)]  
  
3.  という名前のクラスを追加`TodoTag`します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#8)]
     [!code-vb[VSSDKTodoGlyphTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#8)]  
  
4.  という名前のクラスを変更`TodoTagger`を実装する<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>型の`TodoTag`します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#9)]
     [!code-vb[VSSDKTodoGlyphTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#9)]  
  
5.  `TodoTagger`クラスのプライベート フィールドを追加、<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>して、分類内で検索するテキストにまたがっています。  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#10)]
     [!code-vb[VSSDKTodoGlyphTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#10)]  
  
6.  分類子を設定するコンス トラクターを追加します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#11)]
     [!code-vb[VSSDKTodoGlyphTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#11)]  
  
7.  実装、<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>すべての分類を検索して特定のメソッドにわたる名前は「コメント」という単語を含めるし、テキストが検索テキストが含まれています。 検索テキストが見つかったときに、新しい yield 戻る<xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>型の`TodoTag`します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#12)]
     [!code-vb[VSSDKTodoGlyphTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#12)]  
  
8.  宣言を`TagsChanged`イベント。  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#13)]
     [!code-vb[VSSDKTodoGlyphTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#13)]  
  
9. という名前のクラスを追加`TodoTaggerProvider`を実装する<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>、およびエクスポートして、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "code"の<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>TodoTag の。  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#14)]
     [!code-vb[VSSDKTodoGlyphTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#14)]  
  
10. インポート、<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#15)]
     [!code-vb[VSSDKTodoGlyphTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#15)]  
  
11. 実装、<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>メソッドをインスタンス化して、`TodoTagger`します。  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#16)]
     [!code-vb[VSSDKTodoGlyphTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#16)]  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
 このコードをテストするには、TodoGlyphTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>ビルドして TodoGlyphTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  F5 キーを押してプロジェクトを実行します。 Visual Studio の 2 番目のインスタンスがインスタンス化されます。  
  
3.  インジケーター マージンが表示されていることを確認します。 (上、**ツール** メニューのをクリックして**オプション**します。 **テキスト エディター**ことを確認します ページで、**インジケーター マージン**が選択されている)。  
  
4.  コメントのあるコード ファイルを開きます。 コメントのセクションでは、のいずれかに"todo"という単語を追加します。  
  
5.  濃い青のアウトラインが、明るい青色の円は、コード ウィンドウの左側に、インジケーター マージンに表示されます。

