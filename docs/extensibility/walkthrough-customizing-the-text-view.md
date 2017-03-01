---
title: "チュートリアル: テキスト ビューをカスタマイズする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e40368ed6aaf68b747f19cffe4e378a89ff6c0b5
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-customizing-the-text-view"></a>チュートリアル: テキスト ビューをカスタマイズします。
そのエディター形式マップでは、次のプロパティのいずれかを変更することで、テキスト ビューをカスタマイズできます。  
  
-   インジケーター マージン  
  
-   挿入記号  
  
-   キャレットを上書き  
  
-   選択したテキスト  
  
-   選択したテキストの非アクティブな (つまり、選択したテキストがフォーカスを失ったを)  
  
-   可視の空白  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="creating-a-mef-project"></a>MEF プロジェクトを作成します。  
  
1.  C# の場合は、VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューションの名前`ViewPropertyTest`します。  
  
2.  エディターの分類子の項目テンプレートをプロジェクトに追加します。 詳細については、次を参照してください。[エディター項目テンプレートを使用して拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)します。  
  
3.  既存のクラス ファイルを削除します。  
  
## <a name="defining-the-content-type"></a>コンテンツの種類を定義します。  
  
1.  クラス ファイルを追加し、名前`ViewPropertyModifier`します。  
  
2.  次の追加`using`ディレクティブ。  
  
     [!code-cs[VSSDKViewPropertyTest&1;](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs) ] 
     [!code-vb [VSSDKViewPropertyTest&1;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3.  という名前のクラスを宣言`TestViewCreationListener` <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>から継承します。 次の属性を持つこのクラスをエクスポートします。  
  
    -   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>このリスナーを適用するコンテンツの種類を指定します。</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>このリスナーのロールを指定します。</xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>  
  
     [!code-cs[VSSDKViewPropertyTest&2;](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest&2;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4.  このクラスで、インポート<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>。</xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>  
  
     [!code-cs[VSSDKViewPropertyTest&3;](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs) ] 
     [!code-vb [VSSDKViewPropertyTest&3;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="changing-the-view-properties"></a>ビューのプロパティを変更します。  
  
1.  実装、<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>メソッド ビューを開いたときに、ビューのプロパティが変更されるようにします</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>。 変更するには、最初に検索、<xref:System.Windows.ResourceDictionary>を検索するビューの側面に対応する</xref:System.Windows.ResourceDictionary>。 リソース ディクショナリの対応するプロパティを変更し、プロパティを設定します。 呼び出しをバッチ処理、<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A>メソッドを呼び出して、<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A>メソッド、プロパティを設定する前にし、<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A>プロパティを設定した後</xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A></xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A></xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A>。  
  
     [!code-cs[VSSDKViewPropertyTest&4;](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs) ] 
     [!code-vb [VSSDKViewPropertyTest&4;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
  
1.  ソリューションをビルドします。  
  
     デバッガーでこのプロジェクトを実行すると、Visual Studio の&2; つ目のインスタンスがインスタンス化されます。  
  
2.  テキスト ファイルを作成し、いくつかのテキストを入力します。  
  
    -   挿入記号はマゼンタをする必要があり、上書きキャレットが青緑色になります。  
  
    -   ライトをする必要があります (テキスト ビューの左側) にインジケーター マージン緑です。  
  
3.  入力したテキストを選択します。 選択したテキストの色が光をする必要がありますピンク色。  
  
4.  テキストを選択したら、テキスト ウィンドウの外側クリックします。 選択したテキストの色はダーク ピンクをする必要があります。  
  
5.  表示されている空白を有効にします。 (上、**編集** メニューをポイント**詳細設定**  をクリックし、**スペースの表示**)。 いくつかのタブは、テキストを入力します。 タブを表す赤い矢印が表示されます。  
  
## <a name="see-also"></a>関連項目  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)
