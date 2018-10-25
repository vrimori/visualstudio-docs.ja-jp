---
title: 'チュートリアル: 対応するかっこの表示 |Microsoft Docs'
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
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a0568060ec19fc24731850b20dc70dfa7a48231d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49247833"
---
# <a name="walkthrough-displaying-matching-braces"></a>チュートリアル: 対応するかっこの表示
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

かっこの一致が一致する中かっこを定義して、キャレットの中かっこのいずれかである場合に対応する中かっこをテキスト マーカーのタグを追加してなどの言語に基づく機能を実装できます。 中かっこを定義するには、言語のコンテキストでまたは独自ファイル名拡張子とコンテンツ タイプを定義し、その型だけにタグを適用できますか ("text") などの既存のコンテンツ タイプにタグを適用することができます。 次のチュートリアルでは、かっこの一致の「テキスト」コンテンツ タイプにタグを適用する方法を示します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) プロジェクトの作成  
  
#### <a name="to-create-a-mef-project"></a>MEF プロジェクトを作成するには  
  
1.  エディター分類子プロジェクトを作成します。 ソリューション `BraceMatchingTest`の名前を指定します。  
  
2.  エディター分類子の項目テンプレートをプロジェクトに追加します。 詳細については、次を参照してください。[エディターの項目テンプレートを使用した拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)です。  
  
3.  既存のクラス ファイルを削除します。  
  
## <a name="implementing-a-brace-matching-tagger"></a>かっこの一致のタガーを実装します。  
 Visual Studio で使用されている 1 つのような効果を強調表示、かっこを取得するには、型のタガーを実装できます<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>します。 次のコードでは、任意の入れ子のレベルのかっこのペアのタガーを定義する方法を示します。 この例で、かっこをペアします。 、および{}タガー コンス トラクターでは、言語仕様で定義される関連するかっこのペアの完全な言語実装で定義されます。  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>かっこの一致のタガーを実装するには  
  
1.  クラス ファイルを追加し、BraceMatching という名前を付けます。  
  
2.  次の名前空間をインポートします。  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#1)]
     [!code-vb[VSSDKBraceMatchingTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#1)]  
  
3.  クラスを定義する`BraceMatchingTagger`から継承する<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>型の<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#2)]
     [!code-vb[VSSDKBraceMatchingTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#2)]  
  
4.  テキスト ビュー、元のバッファーと、現在のスナップショット ポイントおよび中かっこのペアのセットのプロパティを追加します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#3)]
     [!code-vb[VSSDKBraceMatchingTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#3)]  
  
5.  タガー コンス トラクターでプロパティを設定して、ビューの変更イベントをサブスクライブする<xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged>と<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>します。 この例では、例示を目的として、一致するペアも定義されて、コンス トラクターで。  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#4)]
     [!code-vb[VSSDKBraceMatchingTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#4)]  
  
6.  一部として、<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>実装、TagsChanged イベントを宣言します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#5)]
     [!code-vb[VSSDKBraceMatchingTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#5)]  
  
7.  イベント ハンドラーの更新の現在のカレット位置、`CurrentChar`プロパティと TagsChanged イベントを発生します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#6)]
     [!code-vb[VSSDKBraceMatchingTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#6)]  
  
8.  実装、<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>と一致するメソッドの中かっこいずれかが、始めかっこ、または Visual Studio のように、かっこの前の文字の場合、現在の文字。 一致が見つかった場合は、始めかっことかっこの 2 つのタグにこのメソッドがインスタンス化します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#7)]
     [!code-vb[VSSDKBraceMatchingTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#7)]  
  
9. 次のプライベート メソッドは、任意の入れ子のレベルに対応するかっこを検索します。 最初のメソッドは、開いている文字と一致する終了文字を検索します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#8)]
     [!code-vb[VSSDKBraceMatchingTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#8)]  
  
10. 次のヘルパー メソッドは、閉じる文字と一致する、開いている文字を検索します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#9)]
     [!code-vb[VSSDKBraceMatchingTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#9)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>かっこの一致のタガー プロバイダーを実装します。  
 タガーを実装するだけでなくも実装し、タガー プロバイダーをエクスポートする必要があります。 ここでは、プロバイダーのコンテンツの種類は、"text"です。 つまり、かっこの照合、テキスト ファイルのすべての種類で表示されますが、完全な実装がかっこの一致の特定のコンテンツ タイプにのみ適用されます。  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>中かっこの一致するタガー プロバイダーを実装するには  
  
1.  継承するタガー プロバイダーを宣言<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>でエクスポートし、BraceMatchingTaggerProvider という名前を付けます、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text"、<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>の<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>します。  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#10)]
     [!code-vb[VSSDKBraceMatchingTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#10)]  
  
2.  実装、 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> BraceMatchingTagger をインスタンス化するメソッド。  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#11)]
     [!code-vb[VSSDKBraceMatchingTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#11)]  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
 このコードをテストするには、BraceMatchingTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>ビルドして BraceMatchingTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
3.  テキスト ファイルを作成し、対応する中かっこを含むいくつかのテキストを入力します。  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  始め中かっこの前にキャレットを配置すると、その中かっこと一致する、閉じるかっこの両方を強調する必要があります。 閉じる中かっこの直後後にカーソルを配置すると、その中かっこと一致する始めかっこの両方を強調する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: コンテンツの種類とファイル名拡張子とをリンクさせる](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

