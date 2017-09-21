---
title: "チュートリアル: 対応する中かっこの表示 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] 新しい - かっこの一致"
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# チュートリアル: 対応する中かっこの表示
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

中かっこの一致を一致させる中かっこを定義し、キャレットの中かっこの 1 つであるときにテキスト マーカー タグを対応する中かっこに追加などの言語に対応した機能を実装することができます。 中かっこを定義するには、言語のコンテキストでまたは独自ファイル名拡張子とコンテンツ タイプを定義し、その型だけにタグを適用することができますか \("text"\) などの既存のコンテンツ タイプにタグを適用することができます。 次のチュートリアルでは、かっこの一致の「テキスト」コンテンツ タイプにタグを適用する方法を示します。  
  
## 必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
## Managed Extensibility Framework \(MEF\) プロジェクトの作成  
  
#### MEF プロジェクトを作成するには  
  
1.  エディター分類子プロジェクトを作成します。 ソリューションの名前 `BraceMatchingTest`します。  
  
2.  エディターの分類子の項目テンプレートをプロジェクトに追加します。 詳細については、「[エディター項目テンプレートを使用して拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)」を参照してください。  
  
3.  既存のクラス ファイルを削除します。  
  
## タガーに一致する中かっこを実装します。  
 Visual Studio で使用されるものに似た効果を強調表示、中かっこを取得するには、型のタガーを実装できます <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>します。 次のコードでは、任意の入れ子のレベルで中かっこのペアのタガーを定義する方法を示します。 この例では、中かっこのペアを。 {} がタガー コンス トラクターで定義されていて、完全な言語実装の言語仕様に関連する中かっこのペアが定義されます。  
  
#### タガーに一致する中かっこを実装するには  
  
1.  クラス ファイルを追加し、BraceMatching という名前を付けます。  
  
2.  次の名前空間をインポートします。  
  
     [!code-cs[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]  
  
3.  クラスを定義する `BraceMatchingTagger` から継承する <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 型の <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>です。  
  
     [!code-cs[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]  
  
4.  テキスト ビュー、ソース バッファーと、現在のスナップショット ポイントと中かっこのペアのセットのプロパティを追加します。  
  
     [!code-cs[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]  
  
5.  タガー コンス トラクターでプロパティを設定し、ビューの変更イベントをサブスクライブ <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> と <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>です。 この例では説明の目的で、一致するペアも定義されますコンス トラクターで。  
  
     [!code-cs[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]  
  
6.  一部として、 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 実装では、TagsChanged イベントを宣言します。  
  
     [!code-cs[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]  
  
7.  イベント ハンドラーの現在のキャレット位置を更新する、 `CurrentChar` プロパティと TagsChanged イベントの発生します。  
  
     [!code-cs[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]  
  
8.  実装、 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> が始め中かっこまたは前の文字が Visual Studio と同様に、かっこの場合、現在の文字と一致するメソッドかっこいずれかです。 一致が見つかったときに、2 つのタグ、始め中かっこおよびかっこにこのメソッドがインスタンス化します。  
  
     [!code-cs[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]  
  
9. 次のプライベート メソッドは、任意の入れ子のレベルで対応する中かっこを検索します。 最初のメソッドには、開いている文字と一致する終了文字が検索されます。  
  
     [!code-cs[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]  
  
10. 次のヘルパー メソッドは、閉じる文字と一致する、開いている文字を検索します。  
  
     [!code-cs[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]  
  
## 一致タガー プロバイダーを実装します。  
 タガーを実装するだけでなくも実装し、タガー プロバイダーをエクスポートする必要があります。 この場合、プロバイダーのコンテンツの種類は、"text"です。 つまり、かっこの一致がすべての種類のテキスト ファイルに表示されますが、詳細な実装には、中かっこの特定のコンテンツ タイプにのみ一致が適用されます。  
  
#### 中かっこの一致するタガー プロバイダーを実装するには  
  
1.  継承するタガー プロバイダーを宣言 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, BraceMatchingTaggerProvider、という名前、およびエクスポートして、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text"の <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> の <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>です。  
  
     [!code-cs[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]  
  
2.  実装、 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> 、BraceMatchingTagger をインスタンス化するメソッドです。  
  
     [!code-cs[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]  
  
## コードのビルドとテスト  
 このコードをテストするには、BraceMatchingTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### ビルドし、BraceMatchingTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
3.  テキスト ファイルを作成し、対応する中かっこを含むいくつかのテキストを入力します。  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  始め中かっこの前にキャレットを移動したときにその中かっこと一致するかっこの両方は強調表示されます。 閉じる中かっこの直後にカーソルを移動したときにその中かっこと一致する始め中かっこの両方は強調表示されます。  
  
## 参照  
 [チュートリアル: ファイル名拡張子へのコンテンツの種類のリンク](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)