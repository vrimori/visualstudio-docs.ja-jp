---
title: 'チュートリアル: 対応するかっこの表示 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a048ce1e89de65e805d01971de5c4221b13be826
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53956584"
---
# <a name="walkthrough-display-matching-braces"></a>チュートリアル: 対応するかっこの表示
かっこの一致を一致する中かっこを定義し、キャレットの中かっこのいずれかである場合は、対応する中かっこをテキスト マーカー タグを追加するなど、言語ベースの機能を実装します。 言語のコンテキストで中かっこを定義する、ファイル名拡張子とコンテンツの種類を定義、および入力するか、既存のコンテンツの種類 ("text") などに、タグを適用するだけにタグを適用できます。 次のチュートリアルでは、かっこの一致の「テキスト」コンテンツ タイプにタグを適用する方法を示します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールしないでください。 Visual Studio のセットアップのオプション機能として含まれています。 また、後から VS SDK をインストールすることもできます。 詳細については、"[Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)"を参照してください。  
  
## <a name="create-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) プロジェクトを作成します。  
  
#### <a name="to-create-a-mef-project"></a>MEF プロジェクトを作成するには  
  
1.  エディター分類子プロジェクトを作成します。 ソリューション `BraceMatchingTest`の名前を指定します。  
  
2.  エディター分類子の項目テンプレートをプロジェクトに追加します。 詳細については、次を参照してください。[エディターの項目テンプレートを使用した拡張機能を作成する](../extensibility/creating-an-extension-with-an-editor-item-template.md)します。  
  
3.  既存のクラス ファイルを削除します。  
  
## <a name="implement-a-brace-matching-tagger"></a>かっこの一致のタガーを実装します。  
 Visual Studio で使用されている 1 つのような効果を強調表示、かっこを取得するには、型のタガーを実装できます<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>します。 次のコードでは、任意の入れ子のレベルのかっこのペアのタガーを定義する方法を示します。 この例では、の中かっこのペアと{}で完全な言語の実装では、関連する中かっこのペアが言語仕様で定義されますが、タガー コンス トラクターで定義されます。  
  
### <a name="to-implement-a-brace-matching-tagger"></a>かっこの一致のタガーを実装するには  
  
1.  クラス ファイルを追加し、BraceMatching という名前を付けます。  
  
2.  次の名前空間をインポートします。  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]  
  
3.  クラスを定義する`BraceMatchingTagger`から継承する<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>型の<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]  
  
4.  テキスト ビュー、元のバッファー、現在のスナップショット ポイントおよびも中かっこのペアのセットのプロパティを追加します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]  
  
5.  タガー コンス トラクターでプロパティを設定して、ビューの変更イベントをサブスクライブする<xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged>と<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>します。 この例では、例示を目的として、一致するペアも定義されて、コンス トラクターで。  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]  
  
6.  一部として、<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>実装、TagsChanged イベントを宣言します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]  
  
7.  イベント ハンドラーの更新の現在のカレット位置、`CurrentChar`プロパティと TagsChanged イベントを発生します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]  
  
8.  実装、<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>と一致するメソッドの中かっこいずれかが、始めかっこ、または Visual Studio のように、かっこの前の文字の場合、現在の文字。 一致が見つかった場合は、始めかっことかっこの 2 つのタグにこのメソッドがインスタンス化します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]  
  
9. 次のプライベート メソッドは、任意の入れ子のレベルに対応するかっこを検索します。 最初のメソッドは、開いている文字と一致する終了文字を検索します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]  
  
10. 次のヘルパー メソッドは、閉じる文字と一致する、開いている文字を検索します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]  
  
## <a name="implement-a-brace-matching-tagger-provider"></a>中かっこの一致するタガー プロバイダーを実装します。  
 タガーを実装するだけでなくも実装し、タガー プロバイダーをエクスポートする必要があります。 ここでは、プロバイダーのコンテンツの種類は、"text"です。 そのため、かっこの照合、テキスト ファイルのすべての種類で表示されますが、完全な実装がかっこの一致の特定のコンテンツ タイプにのみ適用されます。  
  
### <a name="to-implement-a-brace-matching-tagger-provider"></a>中かっこの一致するタガー プロバイダーを実装するには  
  
1.  継承するタガー プロバイダーを宣言<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>でエクスポートし、BraceMatchingTaggerProvider という名前を付けます、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text"、<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>の<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]  
  
2.  実装、 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> BraceMatchingTagger をインスタンス化するメソッド。  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]  
  
## <a name="build-and-test-the-code"></a>ビルドし、コードのテスト  
 このコードをテストするには、BraceMatchingTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>ビルドして BraceMatchingTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行する場合は、Visual Studio の 2 番目のインスタンスが開始します。  
  
3.  テキスト ファイルを作成し、対応する中かっこを含むいくつかのテキストを入力します。  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  始め中かっこの前にキャレットを配置すると、その中かっこと一致する、閉じるかっこの両方を強調する必要があります。 閉じる中かっこの直後後にカーソルを配置すると、その中かっこと一致する始めかっこの両方を強調する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: コンテンツの種類をファイル名拡張子にリンクさせる](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)