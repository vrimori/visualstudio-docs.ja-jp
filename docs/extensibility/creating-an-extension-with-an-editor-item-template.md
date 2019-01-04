---
title: エディターの項目テンプレートを使用した拡張機能の作成 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ffaadb2ccdf770231abcbbcc5e594644b78ef7e1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53957866"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>エディターの項目テンプレートを使用した拡張機能を作成します。
エディターに分類子、表示要素、および余白を追加する基本的なエディター拡張機能を作成する Visual Studio SDK に含まれている項目テンプレートを使用することができます。 エディターの項目テンプレートは、Visual c# または Visual Basic の VSIX プロジェクトで使用可能です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 詳細については、"[Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)"を参照してください。  
  
## <a name="create-a-classifier-extension"></a>分類子の拡張機能を作成します。  
 エディター分類子の項目テンプレートは、適切なテキストの色エディター分類子を作成します (この場合、すべてのもの) で任意のテキスト ファイル。  
  
1.  **新しいプロジェクト** ダイアログ ボックスで、展開**Visual c#** または**Visual Basic**順にクリックします**Extensibility**します。 **テンプレート**ペインで、 **VSIX プロジェクト**します。 **[名前]** ボックスに「 `TestClassifier`」と入力します。 **[OK]** をクリックします。  
  
2.  **ソリューション エクスプ ローラー**でプロジェクト ノードを右クリックし、選択**追加** > **新しい項目の**します。 移動する、Visual c#**拡張**ノード**エディター分類子**します。 既定のファイル名のままに (*EditorClassifier1.cs*)。  
  
3.  次のコード ファイルを 4 つがあります。  
  
    -   *EditorClassifier1.cs*が含まれています、`EditorClassifier1`クラス。  
  
    -   *EditorClassifier1ClassificationDefinition.cs*が含まれています、`EditorClassifier1ClassificationDefinition`クラス。  
  
    -   *EditorClassifier1Format.cs*が含まれています、`EditorClassifier1Format`クラス。  
  
    -   *EditorClassifier1Provider.cs*が含まれています、`EditorClassifier1Provider`クラス。  
  
4.  プロジェクトをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスが表示されます。  
  
     テキスト ファイルを開く場合、すべてのテキストは紫色の背景に対する下線が付きます。  
  
## <a name="create-a-text-relative-adornment-extension"></a>相対パスのテキストの表示要素の拡張機能を作成します。  
 エディターのテキストの表示要素のテンプレートは、テキスト文字のすべてのインスタンスを装飾する相対パスのテキストの表示要素を作成します。 赤色の枠と青色の背景を持つボックスを使用して ' a'。 テキストの相対はため、ボックス オーバーレイ 'a' 文字、移動または再フォーマットされる場合でも常にします。  
  
1.  **新しいプロジェクト** ダイアログ ボックスで、展開**Visual c#** または**Visual Basic**順にクリックします**Extensibility**します。 **テンプレート**ペインで、 **VSIX プロジェクト**します。 **[名前]** ボックスに「 `TestAdornment`」と入力します。 **[OK]** をクリックします。  
  
2.  **ソリューション エクスプ ローラー**でプロジェクト ノードを右クリックし、選択**追加** > **新しい項目の**します。 移動する、Visual c#**拡張**ノード**エディターのテキストの表示要素**します。 既定のファイル名のままに (*TextAdornment1.cs/vb*)。  
  
3.  次のように、2 つのコード ファイルがあります。  
  
    -   *TextAdornment1.cs*が含まれています、`TextAdornment1`クラス。  
  
    -   *TextAdornment1TextViewCreationListener.cs*が含まれています、`TextAdornment1TextViewCreationListener`クラス。  
  
4.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。 テキスト ファイルを開く場合、テキストの 'a' すべての文字の輪郭が青色の背景に対して赤に設定します。  
  
## <a name="create-a-viewport-relative-adornment-extension"></a>ビューポートを基準の表示要素の拡張機能を作成します。  
 エディターのビューポートの表示要素のテンプレートは、ビューポートの右上隅に赤色の枠のあるバイオレット ボックスを追加する相対ビューポート表示要素を作成します。  
  
> [!NOTE]
>  **ビューポート**は現在表示されているテキスト ビューの領域です。  
  
### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>エディターのビューポートの表示要素のテンプレートを使用してビューポートの表示要素の拡張機能を作成するには  
  
1.  **新しいプロジェクト** ダイアログ ボックスで、展開**Visual c#** または**Visual Basic**順にクリックします**Extensibility**します。 **テンプレート**ペインで、 **VSIX プロジェクト**します。 **[名前]** ボックスに「 `ViewportAdornment`」と入力します。 **[OK]** をクリックします。  
  
2.  **ソリューション エクスプ ローラー**でプロジェクト ノードを右クリックし、選択**追加** > **新しい項目の**します。 移動する、Visual c#**拡張**ノード**エディターのビューポートの表示要素**します。 既定のファイル名のままに (*ViewportAdornment1.cs/vb*)。  
  
3.  次のように、2 つのコード ファイルがあります。  
  
    -   *ViewportAdornment1.cs*が含まれています、`ViewportAdornment1`クラス。  
  
    -   *ViewportAdornment1TextViewCreationListener.cs*が含まれています、`ViewportAdornment1TextViewCreationListener`クラス  
  
4.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。 新しいテキスト ファイルを作成する場合は、ビューポートの右上隅にある赤色の枠のあるバイオレット ボックスが表示されます。  
  
## <a name="create-a-margin-extension"></a>余白の拡張機能を作成します。  
 エディターの余白テンプレートでは、単語と共に表示される緑の余白を作成します **Hello world!。* 水平スクロール バーの下。  
  
### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>エディターの余白のテンプレートを使用して余白の拡張機能を作成するには  
  
1.  **新しいプロジェクト** ダイアログ ボックスで、展開**Visual c#** または**Visual Basic**順にクリックします**Extensibility**します。 **テンプレート**ペインで、 **VSIX プロジェクト**します。 **[名前]** ボックスに「 `MarginExtension`」と入力します。 **[OK]** をクリックします。  
  
2.  **ソリューション エクスプ ローラー**でプロジェクト ノードを右クリックし、選択**追加** > **新しい項目の**します。 移動する、Visual c#**拡張**ノード**エディター余白**します。 既定のファイル名 (EditorMargin1.cs/vb) のままにします。  
  
3.  次のように、2 つのコード ファイルがあります。  
  
    -   *EditorMargin1.cs*が含まれています、`EditorMargin1`クラス。  
  
    -   *EditorMargin1Factory.cs*が含まれています、`EditorMargin1Factory`クラス。  
  
4.  このプロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。 単語が緑の余白をテキスト ファイルを開くかどうか**こんにちは EditorMargin1**が水平スクロール バーの下に表示されます。  
  
## <a name="see-also"></a>関連項目  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)
