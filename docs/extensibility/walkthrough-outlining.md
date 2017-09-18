---
title: "チュートリアル: アウトラインの中止] | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] 新しい - アウトラインの中止]"
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 30
---
# チュートリアル: アウトラインの中止]
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

展開または折りたたむテキスト領域の種類を定義することでアウトライン表示などの機能の言語に対応したを実装することができます。 領域を定義するには、言語サービスのコンテキストで、または独自ファイル名拡張子とコンテンツ タイプを定義し、その型だけに領域の定義を適用することができます。 または"text"\) などの既存のコンテンツ タイプに領域の定義を適用できます。 このチュートリアルでは、定義のアウトライン領域を表示する方法を示します。  
  
## 必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
## Managed Extensibility Framework \(MEF\) プロジェクトの作成  
  
#### MEF プロジェクトを作成するには  
  
1.  VSIX プロジェクトを作成します。 ソリューションの名前 `OutlineRegionTest`します。  
  
2.  エディターの分類子の項目テンプレートをプロジェクトに追加します。 詳細については、「[エディター項目テンプレートを使用して拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)」を参照してください。  
  
3.  既存のクラス ファイルを削除します。  
  
## アウトライン タガーを実装します。  
 タグの種類でのアウトライン領域が示されます \(<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>\)。 このタグは、標準の動作をアウトライン表示を提供します。 アウトライン表示の領域を展開または折りたたむことができます。 展開すると、その展開された領域が垂直線で区分、アウトライン表示の領域は折りたたまれている場合は、プラス記号またはマイナス記号でマークされます。  
  
 次の手順で区切られたすべての地域のアウトライン領域を作成するタガーを定義する方法を説明する"\["および"\]"です。  
  
#### アウトライン タガーを実装するには  
  
1.  クラス ファイルを追加し、名前 `OutliningTagger`します。  
  
2.  次の名前空間をインポートします。  
  
     [!code-cs[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]  
  
3.  という名前のクラスを作成する `OutliningTagger`, を実装して <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-cs[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]  
  
4.  テキスト バッファーとスナップショットを追跡し、アウトライン領域としてタグ付けするかの行のセットを蓄積するいくつかのフィールドを追加します。 このコードには、\(後で定義\) にアウトライン領域を表す領域オブジェクトの一覧が含まれています。  
  
     [!code-cs[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]  
  
5.  バッファーを解析し、イベント ハンドラーを追加、フィールドを初期化するタガー コンス トラクターを追加、 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> イベントです。  
  
     [!code-cs[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]  
  
6.  実装、 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> タグをインスタンス化するメソッドにわたます。 この例では、内の範囲、 <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> 、メソッドに渡されるは隣接しており、常に大文字と小文字とは限りません。 このメソッドは、アウトラインの地域のそれぞれの新しいタグの範囲をインスタンス化します。  
  
     [!code-cs[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]  
  
7.  宣言、 `TagsChanged` イベント ハンドラーです。  
  
     [!code-cs[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]  
  
8.  追加、 `BufferChanged` に応答するイベント ハンドラー <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> イベント バッファーにテキストを解析しています。  
  
     [!code-cs[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]  
  
9. バッファーを解析するメソッドを追加します。 ここに示す例では、例示のみを目的です。 同期的にバッファーを入れ子になったのアウトライン領域に解析します。  
  
     [!code-cs[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]  
  
10. 次のヘルパー メソッドは、1 が一番左中かっこの対になるように、アウトラインのレベルを表す整数を取得します。  
  
     [!code-cs[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]  
  
11. 次のヘルパー メソッドは、\(このトピックの後半で定義される\) の領域を SnapshotSpan に変換します。  
  
     [!code-cs[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]  
  
12. 次のコードでは、例示のみを目的です。 行番号と、アウトライン領域とも \(存在する場合\) の親領域への参照の開始オフセットを含む PartialRegion クラスを定義します。 これにより、アウトライン領域を入れ子になったパーサーを設定できます。 派生 Region クラスには、アウトライン領域の最後の行番号への参照が含まれています。  
  
     [!code-cs[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]  
  
## タガー プロバイダーを実装します。  
 タガーのタガー プロバイダーをエクスポートする必要があります。 タガー プロバイダーによって作成され、 `OutliningTagger` の「テキスト」コンテンツの種類または他の返品のバッファー、 `OutliningTagger` 1 つは、バッファーが既に存在する場合。  
  
#### タガー プロバイダーを実装するには  
  
1.  という名前のクラスを作成する `OutliningTaggerProvider` を実装する <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, 、エクスポートして、コンテンツ タイプおよび TagType 属性です。  
  
     [!code-cs[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]  
  
2.  実装、 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> メソッドを追加することで、 `OutliningTagger` バッファーのプロパティにします。  
  
     [!code-cs[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]  
  
## コードのビルドとテスト  
 このコードをテストするには、OutlineRegionTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### ビルドし、OutlineRegionTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
3.  テキスト ファイルを作成します。 左中かっこと右中かっこの両方を含む任意のテキストを入力します。  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  両方の中かっこを含むアウトライン領域を設定する必要があります。 アウトライン領域を折りたたむには、始め中かっこの左側にマイナス記号をクリックすることができます。 ときに、領域は折りたたまれ、省略記号 \(...\)、折りたたまれた領域とテキストを含むポップアップの左に記述する必要があります **ホバー テキスト** 、省略記号ボタン上にポインターを移動すると表示されます。  
  
## 参照  
 [チュートリアル: ファイル名拡張子へのコンテンツの種類のリンク](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)