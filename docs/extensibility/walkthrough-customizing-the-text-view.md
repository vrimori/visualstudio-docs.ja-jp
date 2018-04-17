---
title: 'チュートリアル: テキスト ビューをカスタマイズする |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4fb4762a422102b91c44d755d387168ab0572f2a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-customizing-the-text-view"></a>チュートリアル: テキスト ビューをカスタマイズします。
テキスト ビューをカスタマイズするには、そのエディター形式のマップでは、次のプロパティのいずれかの変更します。  
  
-   インジケーター マージン  
  
-   挿入記号  
  
-   カレットを上書き  
  
-   選択したテキスト  
  
-   選択したテキストの非アクティブな (つまり、選択したテキストがフォーカスを失ったを)  
  
-   表示の空白文字  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-mef-project"></a>MEF プロジェクトを作成します。  
  
1.  C# の場合は、VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューションの名前を付けます`ViewPropertyTest`です。  
  
2.  エディター分類子項目テンプレートをプロジェクトに追加します。 詳細については、次を参照してください。[エディター項目テンプレートに、拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)です。  
  
3.  既存のクラス ファイルを削除します。  
  
## <a name="defining-the-content-type"></a>コンテンツの種類を定義します。  
  
1.  クラス ファイルを追加し、名前を付けます`ViewPropertyModifier`です。  
  
2.  次の追加`using`ディレクティブ。  
  
     [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
     [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3.  という名前のクラスを宣言`TestViewCreationListener`から継承する<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>です。 次の属性を持つこのクラスをエクスポートします。  
  
    -   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> このリスナーを適用するコンテンツの種類を指定します。  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> このリスナーのロールを指定します。  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4.  このクラスでは、インポート、<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>です。  
  
     [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
     [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="changing-the-view-properties"></a>ビューのプロパティを変更します。  
  
1.  実装、<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>メソッド ビューを開いたときに、表示のプロパティが変更されるようにします。 変更を行うには、まず検索、<xref:System.Windows.ResourceDictionary>を検索するビューの縦横比に対応します。 リソース ディクショナリで適切なプロパティを変更し、プロパティを設定します。 呼び出しをバッチ処理、<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A>メソッドを呼び出して、<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A>メソッド、プロパティを設定する前にし、<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A>プロパティを設定した後です。  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
  
1.  ソリューションをビルドします。  
  
     デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
2.  テキスト ファイルを作成し、いくつかのテキストを入力します。  
  
    -   挿入記号マゼンタ、上書きカレットは水色をする必要があります。  
  
    -   光をする必要があります (テキスト ビューの左側) のインジケーター マージン緑です。  
  
3.  入力したテキストを選択します。 選択したテキストの色が薄いをする必要がありますピンク色。  
  
4.  テキストを選択しての外側をクリックして、[テキスト] ウィンドウ。 選択したテキストの色は、暗いピンクをする必要があります。  
  
5.  表示スペースを入れます。 (上、**編集** メニューのをポイント**詳細設定**  をクリックし、**スペースの表示**)。 テキストの一部のタブを入力します。 タブを表す赤色の矢印が表示されます。  
  
## <a name="see-also"></a>関連項目  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)