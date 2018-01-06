---
title: "チュートリアル: 中かっこの一致の表示 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c3dde61c10d0a8c9fc5578b02cc713f648409cbf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-displaying-matching-braces"></a>チュートリアル: 対応する中かっこを表示します。
かっこの照合して、照合するかっこを定義するテキスト マーカー タグ キャレットの中かっこの 1 つである場合に対応する中かっこを追加しなどの言語に対応した機能を実装できます。 中かっこを定義するには、言語のコンテキストでまたは独自ファイル名拡張子とコンテンツの種類を定義し、その型にタグを適用することができますか、既存のコンテンツの種類 ("text") などにタグを適用することができます。 次のチュートリアルでは、かっこの一致の「テキスト」コンテンツ タイプにタグを適用する方法を示します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールするはできません。 Visual Studio のセットアップのオプション機能として含まれます。 後でまた VS SDK をインストールすることができます。 詳細については、次を参照してください。 [、Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) プロジェクトの作成  
  
#### <a name="to-create-a-mef-project"></a>MEF プロジェクトを作成するには  
  
1.  エディター分類子プロジェクトを作成します。 ソリューションの名前を付けます`BraceMatchingTest`です。  
  
2.  エディター分類子項目テンプレートをプロジェクトに追加します。 詳細については、次を参照してください。[エディター項目テンプレートに、拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)です。  
  
3.  既存のクラス ファイルを削除します。  
  
## <a name="implementing-a-brace-matching-tagger"></a>一致タガーを実装します。  
 Visual Studio で使用されているいずれかのような効果を強調表示、かっこを得るには、型のタガーを実装することができます<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>です。 次のコードでは、任意の入れ子のレベルのかっこのペアのタガーを定義する方法を示します。 この例では、中かっこをペアします。 、{} がタガー コンス トラクターで定義されていて、完全な言語の実装の言語仕様に関連する中かっこのペアが定義されます。  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>一致タガーを実装するには  
  
1.  クラス ファイルを追加し、BraceMatching という名前を付けます。  
  
2.  次の名前空間をインポートします。  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]  
  
3.  クラスを定義する`BraceMatchingTagger`から継承する<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>型の<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]  
  
4.  テキスト ビュー、ソース バッファーと、現在のスナップショット ポイントと中かっこのペアのセットのプロパティを追加します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]  
  
5.  タガー コンス トラクターでプロパティを設定し、ビューの変更イベントをサブスクライブ<xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged>と<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>です。 この例ではわかりやすくするため、一致するペアもで定義されて、コンス トラクターです。  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]  
  
6.  一部として、<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>実装では、TagsChanged イベントを宣言します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]  
  
7.  イベント ハンドラーは、更新の現在のキャレット位置、`CurrentChar`プロパティおよび TagsChanged イベントを発生します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]  
  
8.  実装、<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>メソッドに一致する右中かっこいずれかが始め中かっこまたは前の文字が Visual Studio と同様に、かっこの場合、現在の文字です。 一致が見つかった場合、このメソッドには、2 つのタグ、始め中かっこおよびかっこがインスタンス化します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]  
  
9. 次のプライベート メソッドでは、任意の入れ子のレベルの対応する中かっこを検索します。 最初のメソッドは、開いている文字と一致する終了文字を検索します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]  
  
10. 次のヘルパー メソッドは、閉じる文字と一致する、開いている文字を検索します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>タガー プロバイダーに一致する中かっこを実装します。  
 タガーを実装するだけでなくも実装し、タガー プロバイダーをエクスポートする必要があります。 この場合、プロバイダーのコンテンツの種類は、"text"です。 これは、かっこの照合のテキスト ファイルのすべての種類で表示されますが、詳細な実装がかっこの一致の特定のコンテンツ タイプにのみに適用されることを意味します。  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>中かっこの一致するタガー プロバイダーを実装するには  
  
1.  継承するタガー プロバイダーの宣言<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>し BraceMatchingTaggerProvider、という名前を使用してエクスポート、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text"、および<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>の<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]  
  
2.  実装、 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> BraceMatchingTagger をインスタンス化するメソッド。  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
 このコードをテストするには、BraceMatchingTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>ビルドし、BraceMatchingTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
3.  テキスト ファイルを作成し、対応する中かっこを含むいくつかのテキストを入力します。  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  始め中かっこの前にキャレットを配置するときにその中かっこと一致するかっこの両方は強調表示されます。 カーソルを閉じる中かっこの直後にすると、その中かっこと一致する始め中かっこの両方は強調表示されます。  
  
## <a name="see-also"></a>参照  
 [チュートリアル: コンテンツの種類とファイル名拡張子とをリンクさせる](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)