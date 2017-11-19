---
title: "チュートリアル: アウトライン |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f503d9e8b0ef125fdb72ea60a9928f308b900993
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-outlining"></a>チュートリアル: アウトライン
展開または折りたたむテキスト領域の種類を定義することでのアウトライン表示などの機能の言語に基づくを実装することができます。 言語サービスのコンテキストで領域を定義することができます独自ファイル名拡張子とコンテンツの種類を定義し、その型だけに領域の定義を適用できます。 または"text") などの既存のコンテンツ タイプに領域の定義を適用することができます。 このチュートリアルでは、定義のアウトライン領域を表示する方法を示します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールするはできません。 Visual Studio のセットアップのオプション機能として含まれます。 後でまた VS SDK をインストールすることができます。 詳細については、次を参照してください。 [、Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) プロジェクトの作成  
  
#### <a name="to-create-a-mef-project"></a>MEF プロジェクトを作成するには  
  
1.  VSIX プロジェクトを作成します。 ソリューションの名前を付けます`OutlineRegionTest`です。  
  
2.  エディター分類子項目テンプレートをプロジェクトに追加します。 詳細については、次を参照してください。[エディター項目テンプレートに、拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)です。  
  
3.  既存のクラス ファイルを削除します。  
  
## <a name="implementing-an-outlining-tagger"></a>アウトラインのタガーを実装します。  
 タグの種類でのアウトライン領域が示されます (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>)。 このタグは、標準の動作をアウトライン表示を提供します。 アウトライン表示の領域を展開または折りたたむことができます。 展開されているし、展開された領域が縦線で demarcated 場合、アウトライン表示の領域は折りたたまれている場合は、プラス記号またはマイナス記号によってマークされます。  
  
 次の手順で区切られたすべての領域のアウトライン領域を作成するタガーを定義する方法を表示する"["および"]"です。  
  
#### <a name="to-implement-an-outlining-tagger"></a>アウトラインのタガーを実装するには  
  
1.  クラス ファイルを追加し、名前を付けます`OutliningTagger`です。  
  
2.  次の名前空間をインポートします。  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]  
  
3.  という名前のクラスを作成する`OutliningTagger`を実装して<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]  
  
4.  テキスト バッファーとスナップショットを追跡し、アウトライン領域としてタグ付けするか行のセットを蓄積するいくつかのフィールドを追加します。 このコードには、(後で定義) にアウトライン領域を表す領域オブジェクトの一覧が含まれています。  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]  
  
5.  バッファーを解析し、イベント ハンドラーを追加、フィールドを初期化するタガー コンス トラクターを追加、<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>イベント。  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]  
  
6.  実装、<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>タグをインスタンス化するメソッドにわたるです。 この例では、範囲、<xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection>メソッドに渡されたできませんが、これが常に大文字と小文字は、連続する、します。 このメソッドは、アウトラインの地域のそれぞれの新しいタグの範囲をインスタンス化します。  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]  
  
7.  宣言、`TagsChanged`イベント ハンドラー。  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]  
  
8.  追加、`BufferChanged`に応答するイベント ハンドラー<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>テキスト バッファーを解析してイベント。  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]  
  
9. バッファーを解析するメソッドを追加します。 ここに示す例では、例示のみです。 同期的に、入れ子になったのアウトライン領域にバッファーを解析します。  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]  
  
10. 次のヘルパー メソッドは、1 が最も左かっこのペアになるように、アウトラインのレベルを表す整数を取得します。  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]  
  
11. 次のヘルパー メソッドは、(このトピックの後半で定義) の領域を SnapshotSpan に変換します。  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]  
  
12. 次のコードでは、例示のみです。 行番号と、アウトライン領域とも (存在する場合) の親領域への参照の開始のオフセットを含む PartialRegion クラスを定義します。 これにより、アウトライン領域を入れ子になった、パーサーをセットアップできます。 地域の派生クラスには、アウトライン領域の最後の行番号への参照が含まれています。  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]  
  
## <a name="implementing-a-tagger-provider"></a>タガー プロバイダーの実装  
 タガーのタガー プロバイダーをエクスポートする必要があります。 タガー プロバイダーを作成、 `OutliningTagger` 「テキスト」コンテンツの種類やその他を返しますのバッファー、 `OutliningTagger` 1 つは、バッファーが既に存在する場合。  
  
#### <a name="to-implement-a-tagger-provider"></a>タガー プロバイダーを実装するには  
  
1.  という名前のクラスを作成する`OutliningTaggerProvider`を実装する<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>、および ContentType と TagType 属性を持つエクスポートします。  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]  
  
2.  実装、<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>メソッドを追加することによって、`OutliningTagger`バッファーのプロパティにします。  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
 このコードをテストするには、OutlineRegionTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>ビルドし、OutlineRegionTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
3.  テキスト ファイルを作成します。 始めかっこと右中かっこの両方を含むいくつかのテキストを入力します。  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  両方の中かっこを含む、アウトライン領域を設定する必要があります。 マイナス記号をクリックして、始めかっこの左側にアウトライン領域を折りたたむことができます。 ときに、領域が折りたたまれている、省略記号 (...)、折りたたまれた領域とテキストを含むポップアップの左側に表示する**ホバー テキスト**省略記号ボタン上にポインターを移動すると表示されます。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: コンテンツの種類とファイル名拡張子とをリンクさせる](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)