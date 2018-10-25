---
title: 'チュートリアル: アウトライン |Microsoft Docs'
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
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0d86dd811339122415a4511b7b7cf28f239be752
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181975"
---
# <a name="walkthrough-outlining"></a>チュートリアル: アウトライン
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

アウトラインの展開または折りたたみをするテキスト領域の種類を定義することでなどの言語ベースの機能を実装できます。 リージョンを定義するには、言語サービスのコンテキストでまたは独自ファイル名拡張子とコンテンツ タイプを定義し、その型だけに領域の定義を適用できますか ("text") などの既存のコンテンツ タイプに領域の定義を適用することができます。 このチュートリアルでは、定義のアウトライン領域を表示する方法を示します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) プロジェクトの作成  
  
#### <a name="to-create-a-mef-project"></a>MEF プロジェクトを作成するには  
  
1.  VSIX プロジェクトを作成します。 ソリューション `OutlineRegionTest`の名前を指定します。  
  
2.  エディター分類子の項目テンプレートをプロジェクトに追加します。 詳細については、次を参照してください。[エディターの項目テンプレートを使用した拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)です。  
  
3.  既存のクラス ファイルを削除します。  
  
## <a name="implementing-an-outlining-tagger"></a>アウトラインのタガーを実装します。  
 アウトライン領域がある種のタグでマークされている (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>)。 このタグは、標準の動作のアウトラインを提供します。 アウトライン表示の領域を展開または折りたたむことができます。 アウトライン表示の領域は折りたたまれている場合は、プラス記号またはマイナス記号によってマークされているが展開されていて、展開された領域が縦線で区分されています。  
  
 次の手順で区切られたすべての領域のアウトライン領域を作成するタガーを定義する方法を表示する"["と"]"。  
  
#### <a name="to-implement-an-outlining-tagger"></a>アウトラインのタガーを実装するには  
  
1.  クラス ファイルを追加し、その名前を `OutliningTagger`にします。  
  
2.  次の名前空間をインポートします。  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#1)]
     [!code-vb[VSSDKOutlineRegionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#1)]  
  
3.  という名前のクラスを作成する`OutliningTagger`、実装すること<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#2)]
     [!code-vb[VSSDKOutlineRegionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#2)]  
  
4.  アウトライン領域としてタグ付けする必要があります行のセットを蓄積して、テキスト バッファーとスナップショットを追跡するためにいくつかのフィールドを追加します。 このコードには、(後で定義) にアウトライン領域を表す領域オブジェクトの一覧が含まれています。  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#3)]
     [!code-vb[VSSDKOutlineRegionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#3)]  
  
5.  バッファーを解析し、イベント ハンドラーを追加、フィールドを初期化するタガー コンス トラクターを追加、<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>イベント。  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#4)]
     [!code-vb[VSSDKOutlineRegionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#4)]  
  
6.  実装、<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>にまたがるメソッドで、タグをインスタンス化します。 この例では、内の範囲、<xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection>メソッドに渡されたこのできない可能性がある場合は、連続するは。 このメソッドは、アウトライン領域の新しいタグの範囲をインスタンス化します。  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#5)]
     [!code-vb[VSSDKOutlineRegionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#5)]  
  
7.  宣言を`TagsChanged`イベント ハンドラー。  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#6)]
     [!code-vb[VSSDKOutlineRegionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#6)]  
  
8.  追加、`BufferChanged`に応答するイベント ハンドラー<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>テキスト バッファーを解析することによってイベント。  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#7)]
     [!code-vb[VSSDKOutlineRegionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#7)]  
  
9. バッファーを解析するメソッドを追加します。 ここに示す例は、例示のみを目的があります。 バッファーは、入れ子になったのアウトライン領域に同期的に解析します。  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#8)]
     [!code-vb[VSSDKOutlineRegionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#8)]  
  
10. 次のヘルパー メソッドは、1 が一番左中かっこのペアになるように、アウトライン レベルを表す整数を取得します。  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#9)]
     [!code-vb[VSSDKOutlineRegionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#9)]  
  
11. 次のヘルパー メソッドは、(このトピックの後半で定義された) 領域を SnapshotSpan に変換します。  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#10)]
     [!code-vb[VSSDKOutlineRegionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#10)]  
  
12. 次のコードでは、例示のみを目的です。 行番号と、アウトライン領域とも (ある場合) の親領域への参照の開始のオフセットを含む PartialRegion クラスを定義します。 これにより、アウトライン領域を入れ子になった、パーサーを設定できます。 リージョンの派生クラスには、アウトライン領域の最後の行番号への参照が含まれています。  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#11)]
     [!code-vb[VSSDKOutlineRegionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#11)]  
  
## <a name="implementing-a-tagger-provider"></a>タガー プロバイダーを実装します。  
 タガーのタガー プロバイダーをエクスポートする必要があります。 タガー プロバイダーを作成、 `OutliningTagger` 「テキスト」コンテンツの種類、または他の返しますのバッファーの場合、 `OutliningTagger` 1 つは、バッファーが既にある場合。  
  
#### <a name="to-implement-a-tagger-provider"></a>タガー プロバイダーを実装するには  
  
1.  という名前のクラスを作成する`OutliningTaggerProvider`を実装する<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>ContentType と TagType 属性を持つエクスポート。  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#12)]
     [!code-vb[VSSDKOutlineRegionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#12)]  
  
2.  実装、<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>メソッドを追加することで、`OutliningTagger`バッファーのプロパティにします。  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#13)]
     [!code-vb[VSSDKOutlineRegionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#13)]  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
 このコードをテストするには、OutlineRegionTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>ビルドして OutlineRegionTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
3.  テキスト ファイルを作成します。 左中かっこと右中かっこの両方を含むいくつかのテキストを入力します。  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  両方の中かっこを含むアウトライン領域が必要です。 始めかっこの左側にアウトライン領域を折りたたむにマイナス記号をクリックする必要があります。 ときに領域が折りたたまれている、省略記号 (...) 折りたたまれた領域とテキストを含むポップアップの左に表示する**ホバー テキスト**省略記号上にポインターを移動するときに表示する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: コンテンツの種類とファイル名拡張子とをリンクさせる](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

