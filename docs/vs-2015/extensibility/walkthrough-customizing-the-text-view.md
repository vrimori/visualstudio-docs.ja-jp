---
title: 'チュートリアル: テキスト ビューのカスタマイズ |Microsoft Docs'
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
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 38cbd0117f5f49666ee5da42d0f60dadf451ffda
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781817"
---
# <a name="walkthrough-customizing-the-text-view"></a>チュートリアル: テキスト ビューのカスタマイズ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

テキスト ビューをカスタマイズするには、そのマップをエディターの書式設定では、次のプロパティのいずれかの変更します。  
  
-   インジケーター マージン  
  
-   キャレットの挿入  
  
-   キャレットを上書き  
  
-   選択したテキスト  
  
-   アクティブでない選択したテキスト (つまり、選択したテキストがフォーカスを失ったを)  
  
-   空白の表示  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-mef-project"></a>MEF プロジェクトを作成します。  
  
1.  C# VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログ ボックスで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューション `ViewPropertyTest`の名前を指定します。  
  
2.  エディター分類子の項目テンプレートをプロジェクトに追加します。 詳細については、次を参照してください。[エディターの項目テンプレートを使用した拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)です。  
  
3.  既存のクラス ファイルを削除します。  
  
## <a name="defining-the-content-type"></a>コンテンツの種類を定義します。  
  
1. クラス ファイルを追加し、その名前を `ViewPropertyModifier`にします。  
  
2. 次の追加`using`ディレクティブ。  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#1)]
    [!code-vb[VSSDKViewPropertyTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#1)]  
  
3. という名前のクラスを宣言`TestViewCreationListener`から継承する<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>します。 このクラスで次の属性をエクスポートします。  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> このリスナーを適用するコンテンツの種類を指定します。  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> このリスナーのロールを指定します。  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#2)]
     [!code-vb[VSSDKViewPropertyTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#2)]  
  
4. このクラスは、インポート、<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>します。  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#3)]
    [!code-vb[VSSDKViewPropertyTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#3)]  
  
## <a name="changing-the-view-properties"></a>ビューのプロパティを変更します。  
  
1.  実装、<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>メソッド ビューを開いたときにビューのプロパティが変更されるようにします。 変更するには、最初に検索、<xref:System.Windows.ResourceDictionary>を検索するビューの側面に対応します。 リソース ディクショナリに適切なプロパティを変更し、プロパティを設定します。 呼び出しをバッチ処理、<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A>メソッドを呼び出して、<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A>メソッド、プロパティを設定する前にし、<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A>プロパティを設定した後。  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#4)]
     [!code-vb[VSSDKViewPropertyTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#4)]  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
  
1.  ソリューションをビルドします。  
  
     デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
2.  テキスト ファイルを作成し、いくつかのテキストを入力します。  
  
    -   挿入記号はマゼンタをする必要があり、上書きキャレットが青緑にする必要があります。  
  
    -   (テキスト ビューの左側) に、インジケーター マージンが光は緑色です。  
  
3.  入力したテキストを選択します。 選択したテキストの色は光はピンク色。  
  
4.  テキストが選択された状態では、テキスト ウィンドウの外側クリックします。 選択したテキストの色を濃いピンクとなります。  
  
5.  空白の表示を有効にします。 (上、**編集**メニューで、**詳細**順にクリックします**スペースの表示**)。 いくつかのタブは、テキストを入力します。 タブを表す赤い矢印が表示されます。  
  
## <a name="see-also"></a>関連項目  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)

