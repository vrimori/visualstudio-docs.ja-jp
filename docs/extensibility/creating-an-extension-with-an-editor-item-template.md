---
title: "エディター項目テンプレートに、拡張機能の作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fb66dfffaf8fa8339ce9060c912dc358fb454a7e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="creating-an-extension-with-an-editor-item-template"></a>エディター項目テンプレートに、拡張機能の作成
エディターに分類子、修飾、および余白を追加する基本的なエディター拡張機能を作成する Visual Studio SDK に含まれている項目テンプレートを使用することができます。 エディターの項目テンプレートは、Visual c# または Visual Basic の VSIX プロジェクトで使用可能です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールするはできません。 Visual Studio のセットアップのオプション機能として含まれます。 後でまた VS SDK をインストールすることができます。 詳細については、次を参照してください。 [、Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="creating-a-classifier-extension"></a>分類器の拡張機能の作成  
 エディター分類子のアイテム テンプレート エディターの分類器を該当するテキストの色を作成する (このケースでは、すべてのもの) 任意のテキスト ファイルにします。  
  
1.  **新しいプロジェクト** ダイアログ ボックスで、展開**Visual c#**または**Visual Basic**  をクリックし、 **Extensibility**です。 **テンプレート**ペインで、 **VSIX プロジェクト**です。 **[名前]** ボックスに「`TestClassifier`」と入力します。 **[OK]**をクリックします。  
  
2.  **ソリューション エクスプ ローラー**プロジェクト ノードを右クリックし、選択、**追加/新しい項目の**します。 移動する、Visual c#**機能拡張**ノード**エディター分類子**です。 既定のファイル名 (EditorClassifier1.cs) のままにします。  
  
3.  次の 3 つのコード ファイルを次があります。  
  
    -   EditorClassifier1.cs が含まれています、`EditorClassifier1`クラスです。  
  
    -   EditorClassifier1ClassificationDefinition.cs が含まれています、`OEditorClassifier1ClassificationDefinition`クラスです。  
  
    -   EditorClassifier1Format.cs が含まれています、`EditorClassifier1Format`クラスです。  
  
    -   EditorClassifier1Provider.cs が含まれています、`EditorClassifier1Provider`クラスです。  
  
4.  プロジェクトをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスが表示されます。  
  
     テキスト ファイルを開くと、紫色の背景に対してすべてのテキストに下線が付けられます。  
  
## <a name="creating-a-text-relative-adornment-extension"></a>テキストの相対表示要素の拡張機能の作成  
 エディターのテキスト装飾テンプレートで作成、テキスト文字のすべてのインスタンスを装飾するテキストの相対装飾赤の輪郭と青色の背景を持つボックスを使用して ' a' です。 テキストの相対であるため、ボックス オーバーレイ 'a' 文字の場合、移動または再フォーマットされる場合でも常にします。  
  
1.  **新しいプロジェクト** ダイアログ ボックスで、展開**Visual c#**または**Visual Basic**  をクリックし、 **Extensibility**です。 **テンプレート**ペインで、 **VSIX プロジェクト**です。 **[名前]** ボックスに「`TestAdornment`」と入力します。 **[OK]**をクリックします。  
  
2.  **ソリューション エクスプ ローラー**プロジェクト ノードを右クリックし、選択、**追加/新しい項目の**します。 移動する、Visual c#**機能拡張**ノード**エディターのテキスト装飾**です。 既定のファイル名 (TextAdornment1.cs/vb) のままにします。  
  
3.  2 つのコード ファイルを次があります。  
  
    -   TextAdornment1.cs が含まれています、`TextAdornment1`クラスです。  
  
    -   extAdornment1TextViewCreationListener.cs が含まれています、`TextAdornment1TextViewCreationListener`クラスです。  
  
4.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。 テキスト ファイルを開く場合、'a' のすべての文字のテキストが青色の背景に対して赤色で説明されています。  
  
## <a name="creating-a-viewport-relative-adornment-extension"></a>ビューポートを基準の表示要素の拡張機能の作成  
 エディターのビューポートの表示要素のテンプレートでは、ビューポートの右上隅に赤いアウトラインが紫ボックスを追加するビューポート相対表示要素を作成します。  
  
> [!NOTE]
>  *ビューポート*現在表示されているテキスト ビューの領域です。  
  
#### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>エディターのビューポートの表示要素のテンプレートを使用してビューポートの表示要素の拡張機能を作成するには  
  
1.  **新しいプロジェクト** ダイアログ ボックスで、展開**Visual c#**または**Visual Basic**  をクリックし、 **Extensibility**です。 **テンプレート**ペインで、 **VSIX プロジェクト**です。 **[名前]** ボックスに「`ViewportAdornment`」と入力します。 **[OK]**をクリックします。  
  
2.  **ソリューション エクスプ ローラー**プロジェクト ノードを右クリックし、選択、**追加/新しい項目の**します。 移動して、Visual c# に**機能拡張**ノード**エディター ビューポート装飾**です。 既定のファイル名 (ViewportAdornment1.cs/vb) のままにします。  
  
3.  2 つのコード ファイルを次があります。  
  
    -   ViewportAdornment1.cs が含まれています、`ViewportAdornment1`クラスです。  
  
    -   ViewportAdornment1TextViewCreationListener.cs が含まれています、`ViewportAdornment1TextViewCreationListener`クラス  
  
4.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。 新しいテキスト ファイルを作成する場合、ビューポートの右上隅にある赤いアウトラインが紫ボックスが表示されます。  
  
## <a name="creating-a-margin-extension"></a>余白の拡張機能の作成  
 エディターのマージン テンプレートは、単語"Hello world!"と表示される緑色の余白を作成します。 水平スクロール バーの下。  
  
#### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>エディターのマージンのテンプレートを使用して余白の拡張機能を作成するには  
  
1.  **新しいプロジェクト** ダイアログ ボックスで、展開**Visual c#**または**Visual Basic**  をクリックし、 **Extensibility**です。 **テンプレート**ペインで、 **VSIX プロジェクト**です。 **[名前]** ボックスに「`MarginExtension`」と入力します。 **[OK]**をクリックします。  
  
2.  **ソリューション エクスプ ローラー**プロジェクト ノードを右クリックし、選択、**追加/新しい項目の**します。 移動して、Visual c# に**機能拡張**ノード**エディター ビューポート装飾**です。 既定のファイル名 (EditorMargin1.cs/vb) のままにします。  
  
3.  2 つのコード ファイルを次があります。  
  
    -   EditorMargin1.cs が含まれています、`EditorMargin1`クラスです。  
  
    -   EditorMargin1Factory.cs が含まれています、`EditorMargin1Factory`クラスです。  
  
4.  このプロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。 テキスト ファイルを開くと、水平スクロール バーの下を"こんにちは EditorMargin1"という語を持つ緑色の余白が表示されます。  
  
## <a name="see-also"></a>参照  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)