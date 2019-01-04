---
title: 'チュートリアル: テキスト ビューをカスタマイズする |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8748ccade8e610c66d9c4142312c2c5dfed1ddf9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917320"
---
# <a name="walkthrough-customize-the-text-view"></a>チュートリアル: テキスト ビューをカスタマイズします。
テキスト ビューをカスタマイズするには、そのマップをエディターの書式設定では、次のプロパティのいずれかの変更します。  
  
-   インジケーター マージン  
  
-   キャレットの挿入  
  
-   キャレットを上書き  
  
-   選択したテキスト  
  
-   アクティブでない選択したテキスト (つまり、選択したテキストがフォーカスを失ったを)  
  
-   空白の表示  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 Visual Studio のセットアップのオプション機能として含まれています。 また、後から VS SDK をインストールすることもできます。 詳細については、"[Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)"を参照してください。  
  
## <a name="create-a-mef-project"></a>MEF プロジェクトを作成します。  
  
1.  C# VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログ ボックスで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューション `ViewPropertyTest`の名前を指定します。  
  
2.  エディター分類子の項目テンプレートをプロジェクトに追加します。 詳細については、次を参照してください。[エディターの項目テンプレートを使用した拡張機能を作成する](../extensibility/creating-an-extension-with-an-editor-item-template.md)します。  
  
3.  既存のクラス ファイルを削除します。  
  
## <a name="define-the-content-type"></a>コンテンツの種類を定義します。  
  
1. クラス ファイルを追加し、その名前を `ViewPropertyModifier`にします。  
  
2. 次の追加`using`ディレクティブ。  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3. という名前のクラスを宣言`TestViewCreationListener`から継承する<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>します。 このクラスで次の属性をエクスポートします。  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> このリスナーを適用するコンテンツの種類を指定します。  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> このリスナーのロールを指定します。  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4. このクラスは、インポート、<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>します。  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="change-the-view-properties"></a>ビューのプロパティを変更します。  
  
1.  セットアップ、<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>メソッド ビューを開いたときにビューのプロパティが変更されるようにします。 変更するには、最初に検索、<xref:System.Windows.ResourceDictionary>を検索するビューの側面に対応します。 リソース ディクショナリに適切なプロパティを変更し、プロパティを設定します。 呼び出しをバッチ処理、<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A>メソッドを呼び出して、<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A>メソッド、プロパティを設定する前にし、<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A>プロパティを設定した後。  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="build-and-test-the-code"></a>ビルドし、コードのテスト  
  
1.  ソリューションをビルドします。  
  
     デバッガーでこのプロジェクトを実行する場合は、Visual Studio の 2 番目のインスタンスが開始します。  
  
2.  テキスト ファイルを作成し、いくつかのテキストを入力します。  
  
    -   挿入記号はマゼンタをする必要があり、上書きキャレットが青緑にする必要があります。  
  
    -   (テキスト ビューの左側) に、インジケーター マージンが光は緑色です。  
  
3.  入力したテキストを選択します。 選択したテキストの色は光はピンク色。  
  
4.  テキストが選択された状態では、テキスト ウィンドウの外側クリックします。 選択したテキストの色を濃いピンクとなります。  
  
5.  空白の表示を有効にします。 (上、**編集**メニューで、**詳細**順にクリックします**スペースの表示**)。 いくつかのタブは、テキストを入力します。 タブを表す赤い矢印が表示されます。  
  
## <a name="see-also"></a>関連項目  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)