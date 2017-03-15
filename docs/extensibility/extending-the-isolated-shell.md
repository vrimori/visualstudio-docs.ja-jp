---
title: "分離シェルの拡張 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio shell、分離モード"
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 分離シェルの拡張
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

分離された Visual Studio シェルを拡張するには、VSPackage、Managed Extensibility Framework \(MEF\) コンポーネントの一部、または汎用的な VSIX プロジェクトを分離シェル アプリケーションに追加します。  
  
> [!NOTE]
>  次の手順では、Visual Studio シェルの分離のプロジェクト テンプレートを使用して基本的な分離シェル アプリケーションを作成することを前提とします。 このプロジェクト テンプレートの詳細については、次を参照してください。 [チュートリアル: 基本的な分離シェル アプリケーションを作成します。](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)します。  
  
## Visual Studio パッケージのプロジェクト テンプレートの場所  
 Visual Studio パッケージのプロジェクト テンプレートは、**\[新しいプロジェクト\]** ダイアログの次の 3 つの場所にあります。  
  
1.  **Visual Basic**, 、**拡張**します。 プロジェクトの既定の言語は Visual Basic です。  
  
2.  **Visual c\#**, 、**拡張**します。 プロジェクトの既定の言語は C\# です。  
  
3.  **他のプロジェクト タイプ**, 、**拡張**します。 プロジェクトの既定の言語は C\+\+ です。  
  
## VSPackage を追加します。  
 VSPackage は、分離シェル アプリケーションを追加できます。 次の手順では、メニュー コマンドを追加する 1 つを作成する方法を示します。  
  
#### 新しい VSPackage を追加するには  
  
1.  という名前の Visual Studio パッケージ プロジェクトを追加 `MenuCommandsPackage`します。  
  
2.  **VSPackage の基本情報** 、ウィザードのページ設定 **会社名** に `Fabrikam` と **VSPackage 名** に `FabrikamMenuCommands`します。**\[次へ\]** ボタンをクリックします。  
  
3.  次のページで次のように選択します。 **メニュー コマンド** にして **次**します。  
  
4.  次のページで次のように設定します。 **コマンド名** に `Fabrikam Command` と **コマンド ID** に `cmdidFabrikamCommand`, 、を選択し **次**します。  
  
5.  **テスト プロジェクトのオプションを選択** \] ページでテストのオプションをオフにして、選択、 **完了** \] ボタンをクリックします。  
  
6.  ShellExtensionsVSIX プロジェクトの source.extension.vsixmanifest ファイルを開きます。  
  
     **資産** セクションが VSShellStub.AboutBoxPackage プロジェクトのエントリを含める必要があります。  
  
7.  **\[新規作成\]** を選択します。  
  
8.  **新しいアセットの追加** \] ウィンドウで、 **型** 一覧で、\[ **として \[Microsoft.VisualStudio.VsPackage**します。  
  
9. **ソース** ボックスの一覧で、必ず **現在のソリューション内のプロジェクト** が選択されています。**プロジェクト** リスト ボックスで、 **MenuCommandsPackage**します。  
  
10. ファイルを保存して閉じます。  
  
11. ソリューションをリビルドし、分離シェルのデバッグを開始します。  
  
12. メニュー バー **ツール** \] メニューの \[ **Fabrikam コマンド**します。  
  
     メッセージ ボックスが表示されます。  
  
13. アプリケーションのデバッグを停止します。  
  
## MEF コンポーネント パーツを追加します。  
 次の手順では、分離シェル アプリケーションを MEF コンポーネント パーツを追加する方法を示します。  
  
#### MEF コンポーネントを追加するには  
  
1.  **新しいプロジェクトの追加** ダイアログ ボックスで、 **Visual c\#**, 、**拡張**, を使用して、 **エディターのマージン** プロジェクトを追加するテンプレートです。 これに `ShellEditorMargin` という名前を付けます。  
  
2.  ShellExtensionsVSIX プロジェクトでは、コード ビューではなく、デザイン ビューで、Source.extension.vsixmanifest ファイルを開きます。  
  
3.  `Asset` セクションで、選択 **コンテンツの追加**します。  
  
4.  **新しいアセットの追加** ウィンドウで、 **型** 一覧で、\[ **Microsoft.VisualStudio.MefComponent**します。  
  
5.  **ソース** ボックスの一覧で、必ず **現在のソリューション内のプロジェクト** が選択されています。**プロジェクト** リスト ボックスで、 **ShellEditorMargin**します。  
  
6.  ファイルを保存して閉じます。  
  
7.  ソリューションをリビルドし、分離シェルのデバッグを開始します。  
  
8.  テキスト ファイルを開きます。  
  
     "Hello world\!"という語句を含んでいる緑色の余白 テキスト ファイル ウィンドウの下部に表示する必要があります。  
  
9. アプリケーションのデバッグを停止します。  
  
## 一般的な VSIX プロジェクトを追加します。  
  
#### 一般的な VSIX プロジェクトに追加するには  
  
1.  **新しいプロジェクトの追加** ダイアログ ボックスで、 **Visual c\#**, 、**拡張**, を使用して、 **VSIXProject** プロジェクトを追加するテンプレートです。 これに `EmptyVSIX` という名前を付けます。  
  
2.  ShellExtensionsVSIX プロジェクトでは、コード ビューではなく、デザイン ビューで Source.extensions.vsixmanifest ファイルを開きます。  
  
3.  `Assets` セクションで、選択 **新規**します。  
  
4.  **新しいアセットの追加** \] ウィンドウで、 **型** 一覧で、追加するコンテンツの種類を選択します。  
  
5.  **ソース**, 、ことを確認して、 **現在のソリューション内のプロジェクト** オプションを選択します。 リスト ボックスで、VSIX プロジェクトの名前を選択します。  
  
6.  ファイルを保存して閉じます。  
  
7.  このプロジェクトには、コンパイルされたコードが含まれている場合は、アセンブリが出力に含まれるようプロジェクトを編集する必要があります。  
  
    1.  VSIX プロジェクトをアンロードし、プロジェクト ファイルを開きます。  
  
    2.  最初の `<PropertyGroup>` の値を変更する、ブロック `<CopyBuildOutputToOutputDirectory>` に `true`します。  
  
    3.  保存し、プロジェクトの再読み込みします。  
  
8.  ソリューションをビルドして実行します。  
  
## 参照  
 [チュートリアル: 基本的な分離シェル アプリケーションを作成します。](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)