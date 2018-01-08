---
redirect_url: shell/extending-the-isolated-shell
title: "分離シェルを拡張 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fffa21e0351b6516920700d8dde0ba8b43243a9a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-isolated-shell"></a>分離シェルの拡張
Visual Studio 分離シェルを拡張するには、VSPackage、Managed Extensibility Framework (MEF) コンポーネント パーツ、または汎用的な VSIX プロジェクトを分離シェル アプリケーションに追加します。  
  
> [!NOTE]
>  次の手順では、Visual Studio 分離シェルのプロジェクト テンプレートを使用して基本的な分離シェル アプリケーションを作成したことを前提とします。 このプロジェクト テンプレートの詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)です。  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio パッケージのプロジェクト テンプレートの場所  
 Visual Studio パッケージのプロジェクト テンプレートは、 **[新しいプロジェクト]** ダイアログの次の 3 つの場所にあります。  
  
1.  **Visual Basic**、 **Extensibility**です。 プロジェクトの既定の言語は Visual Basic です。  
  
2.  **Visual c#**、 **Extensibility**です。 プロジェクトの既定の言語は C# です。  
  
3.  **他のプロジェクト タイプ**、 **Extensibility**です。 プロジェクトの既定の言語は C++ です。  
  
## <a name="adding-a-vspackage"></a>VSPackage を追加します。  
 VSPackage は、分離シェル アプリケーションを追加できます。 次の手順では、メニュー コマンドを追加する 1 つを作成する方法を示します。  
  
#### <a name="to-add-a-new-vspackage"></a>新しい VSPackage を追加するには  
  
1.  という名前の Visual Studio パッケージ プロジェクトを追加`MenuCommandsPackage`です。  
  
2.  **VSPackage の基本情報**、ウィザードのページ設定**会社名**に`Fabrikam`と**VSPackage 名前**に`FabrikamMenuCommands`です。 **[次へ]** ボタンをクリックします。  
  
3.  次のページで次のように選択します。**メニュー コマンド**を選択し**次**です。  
  
4.  次のページで次のように設定します。**コマンド名**に`Fabrikam Command`と**コマンド ID**に`cmdidFabrikamCommand`、を選択し**次**です。  
  
5.  **テスト プロジェクトのオプションを選択** ページで、テストのオプションをオフにして選択し、**完了**ボタンをクリックします。  
  
6.  ShellExtensionsVSIX プロジェクトの source.extension.vsixmanifest ファイルを開きます。  
  
     **資産**セクションが VSShellStub.AboutBoxPackage プロジェクトのエントリを含める必要があります。  
  
7.  選択、**新規**ボタンをクリックします。  
  
8.  **新しいアセットの追加**] ウィンドウで、**型**一覧で、[ **Microsoft.VisualStudio.VsPackage**です。  
  
9. **ソース**一覧で、ことを確認して**、現在のソリューションでプロジェクト**が選択されています。 **プロジェクト**リスト ボックスで、 **MenuCommandsPackage**です。  
  
10. ファイルを保存して閉じます。  
  
11. ソリューションをリビルドし、分離シェルのデバッグを開始します。  
  
12. メニュー バーで、次のように選択します。**ツール**] メニューの [し**Fabrikam コマンド**です。  
  
     メッセージ ボックスが表示されます。  
  
13. アプリケーションのデバッグを停止します。  
  
## <a name="adding-a-mef-component-part"></a>MEF コンポーネント パーツを追加します。  
 次の手順では、分離シェル アプリケーションを MEF コンポーネント パーツを追加する方法を示します。  
  
#### <a name="to-add-a-mef-component"></a>MEF コンポーネントを追加するには  
  
1.  **新しいプロジェクトの追加**ダイアログ ボックスで、 **Visual c#**、 **Extensibility**を使用して、**エディターのマージン**プロジェクトを追加するテンプレートです。 これに `ShellEditorMargin` という名前を付けます。  
  
2.  ShellExtensionsVSIX プロジェクトでは、デザイン ビューで、コード ビューではなく、Source.extension.vsixmanifest ファイルを開きます。  
  
3.  `Asset`セクションで、選択**コンテンツの追加**です。  
  
4.  **新しいアセットの追加**] ウィンドウで、**型**一覧で、[ **Microsoft.VisualStudio.MefComponent**です。  
  
5.  **ソース**一覧で、ことを確認して**、現在のソリューションでプロジェクト**が選択されています。 **プロジェクト**リスト ボックスで、 **ShellEditorMargin**です。  
  
6.  ファイルを保存して閉じます。  
  
7.  ソリューションをリビルドし、分離シェルのデバッグを開始します。  
  
8.  テキスト ファイルを開きます。  
  
     "Hello world!"を含んでいる緑の余白 テキスト ファイル ウィンドウの下部に表示されます。  
  
9. アプリケーションのデバッグを停止します。  
  
## <a name="adding-a-generic-vsix-project"></a>一般的な VSIX プロジェクトを追加します。  
  
#### <a name="to-add-a-generic-vsix-project"></a>一般的な VSIX プロジェクトに追加するには  
  
1.  **新しいプロジェクトの追加**ダイアログ ボックスで、 **Visual c#**、 **Extensibility**を使用して、 **VSIXProject**プロジェクトを追加するテンプレートです。 これに `EmptyVSIX` という名前を付けます。  
  
2.  ShellExtensionsVSIX プロジェクトでは、デザイン ビューで、コード ビューではなく Source.extensions.vsixmanifest ファイルを開きます。  
  
3.  `Assets`セクションで、選択**新規**です。  
  
4.  **新しいアセットの追加** ウィンドウで、**型**一覧で、追加するコンテンツの種類を選択します。  
  
5.  **ソース**、ことを確認して、**現在のソリューション内のプロジェクト**オプションを選択します。 リスト ボックスで、VSIX プロジェクトの名前を選択します。  
  
6.  ファイルを保存して閉じます。  
  
7.  このプロジェクトには、コンパイルされたコードが含まれている場合は、アセンブリは、出力に含まれるように、プロジェクトを編集する必要があります。  
  
    1.  VSIX プロジェクトをアンロードして、プロジェクト ファイルを開きます。  
  
    2.  最初の`<PropertyGroup>`ブロックは、値を変更`<CopyBuildOutputToOutputDirectory>`に`true`です。  
  
    3.  保存し、プロジェクトの再読み込みします。  
  
8.  ソリューションをビルドして実行します。  
  
## <a name="see-also"></a>参照  
 [チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)