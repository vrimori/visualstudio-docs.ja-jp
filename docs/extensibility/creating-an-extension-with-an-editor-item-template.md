---
title: "エディター項目テンプレートを使用して拡張機能の作成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] - 新しい拡張機能"
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# エディター項目テンプレートを使用して拡張機能の作成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

分類子、表示要素、および余白をエディターに追加する基本的なエディター拡張機能を作成する Visual Studio SDK に含まれている項目テンプレートを使用できます。 エディター項目テンプレートは、Visual c\# または Visual Basic の VSIX プロジェクトで使用可能です。  
  
## 必要条件  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
## 分類子の拡張機能の作成  
 エディターの分類子項目テンプレートを該当するテキストの色、エディターの分類器を作成 \(この場合、すべてのもの\) 任意のテキスト ファイルにします。  
  
1.  **新しいプロジェクト** \] ダイアログ ボックスで、展開 **Visual c\#** または **Visual Basic** \] をクリックし、 **機能拡張**します。**テンプレート** \] ウィンドウの \[ **VSIX プロジェクト**します。**名** ボックスに、入力 `TestClassifier`します。**\[OK\]** をクリックします。  
  
2.  **ソリューション エクスプ ローラー**, プロジェクト ノードを右クリックして、選択 **追加\/\[新しい項目の**します。 移動する、Visual c\# **機能拡張** ノード **エディターの分類子**します。 既定のファイル名 \(EditorClassifier1.cs\) のままにします。  
  
3.  次の 3 つのコード ファイルを次があります。  
  
    -   EditorClassifier1.cs を含む、 `EditorClassifier1` クラスです。  
  
    -   EditorClassifier1ClassificationDefinition.cs を含む、 `OEditorClassifier1ClassificationDefinition` クラスです。  
  
    -   EditorClassifier1Format.cs を含む、 `EditorClassifier1Format`  クラスです。  
  
    -   EditorClassifier1Provider.cs を含む、 `EditorClassifier1Provider` クラスです。  
  
4.  プロジェクトをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスが表示されます。  
  
     テキスト ファイルを開くと、紫色の背景に対するすべてのテキスト下線が引かれました。  
  
## テキスト単位の表示要素の拡張機能の作成  
 エディターのテキストの表示要素テンプレートをテキスト文字のすべてのインスタンスを装飾するテキスト単位の表示要素を作成、赤のアウトラインと青色の背景を持つボックスを使用して ' a' です。 テキストの相対であるため、ボックス オーバーレイ 'a' 文字の場合、移動または再フォーマットされる場合でも常にします。  
  
1.  **新しいプロジェクト** \] ダイアログ ボックスで、展開 **Visual c\#** または **Visual Basic** \] をクリックし、 **機能拡張**します。**テンプレート** \] ウィンドウの \[ **VSIX プロジェクト**します。**名** ボックスに、入力 `TestAdornment`します。**\[OK\]** をクリックします。  
  
2.  **ソリューション エクスプ ローラー**, プロジェクト ノードを右クリックして、選択 **追加\/\[新しい項目の**します。 移動する、Visual c\# **拡張** ノード **エディターのテキストの表示要素**します。 既定のファイル名 \(TextAdornment1.cs\/vb\) のままにします。  
  
3.  2 つのコード ファイルを次があります。  
  
    -   TextAdornment1.cs を含む、 `TextAdornment1` クラスです。  
  
    -   extAdornment1TextViewCreationListener.cs を含む、 `TextAdornment1TextViewCreationListener` クラスです。  
  
4.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。 テキスト ファイルを開く場合のすべての 'a' 文字のテキストは赤の中抜きに青色の背景にします。  
  
## ビューポートを基準の表示要素の拡張機能の作成  
 エディターのビューポートの表示要素のテンプレートには、ビューポートの右上隅に赤色のアウトラインが紫のボックスを追加するビューポートを基準の表示要素が作成されます。  
  
> [!NOTE]
>  *ビューポート* は現在表示されているテキスト ビューの領域です。  
  
#### エディターのビューポートの表示要素テンプレートを使用してビューポートの表示要素の拡張機能を作成するには  
  
1.  **新しいプロジェクト** \] ダイアログ ボックスで、展開 **Visual c\#** または **Visual Basic** \] をクリックし、 **機能拡張**します。**テンプレート** \] ウィンドウの \[ **VSIX プロジェクト**します。**名** ボックスに、入力 `ViewportAdornment`します。**\[OK\]** をクリックします。  
  
2.  **ソリューション エクスプ ローラー**, プロジェクト ノードを右クリックして、選択 **追加\/\[新しい項目の**します。 移動する、Visual c\# **拡張** ノード **エディターのビューポートの表示要素**します。 既定のファイル名 \(ViewportAdornment1.cs\/vb\) のままにします。  
  
3.  2 つのコード ファイルを次があります。  
  
    -   ViewportAdornment1.cs を含む、 `ViewportAdornment1` クラスです。  
  
    -   ViewportAdornment1TextViewCreationListener.cs を含む、 `ViewportAdornment1TextViewCreationListener` クラス  
  
4.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。 新しいテキスト ファイルを作成する場合、ビューポートの右上隅にある赤色のアウトラインが紫のボックスが表示されます。  
  
## 余白の拡張機能の作成  
 エディターのマージンのテンプレートは、単語"Hello world\!"と表示される緑色の余白を作成します。 水平スクロール バーの下です。  
  
#### エディターのマージンのテンプレートを使用して余白の拡張機能を作成するには  
  
1.  **新しいプロジェクト** \] ダイアログ ボックスで、展開 **Visual c\#** または **Visual Basic** \] をクリックし、 **機能拡張**します。**テンプレート** \] ウィンドウの \[ **VSIX プロジェクト**します。**名** ボックスに、入力 `MarginExtension`します。**\[OK\]** をクリックします。  
  
2.  **ソリューション エクスプ ローラー**, プロジェクト ノードを右クリックして、選択 **追加\/\[新しい項目の**します。 移動する、Visual c\# **拡張** ノード **エディターのビューポートの表示要素**します。 既定のファイル名 \(EditorMargin1.cs\/vb\) のままにします。  
  
3.  2 つのコード ファイルを次があります。  
  
    -   EditorMargin1.cs を含む、 `EditorMargin1` クラスです。  
  
    -   EditorMargin1Factory.cs を含む、 `EditorMargin1Factory` クラスです。  
  
4.  このプロジェクトをビルドしてデバッグを開始します。 実験用インスタンスが表示されます。 テキスト ファイルを開くと、水平スクロール バーの下を単語の"こんにちは EditorMargin1"を持つ緑色の余白が表示されます。  
  
## 参照  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)