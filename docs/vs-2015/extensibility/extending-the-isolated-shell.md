---
title: 分離シェルの拡張 |Microsoft Docs
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
- Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dc700e0a1b8753a26067eff90df9ff58765de8d1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792022"
---
# <a name="extending-the-isolated-shell"></a>分離シェルの拡張
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage、Managed Extensibility Framework (MEF) コンポーネント パーツ、または汎用的な VSIX プロジェクトを分離シェル アプリケーションに追加することで、Visual Studio 分離シェルを拡張できます。  
  
> [!NOTE]
>  次の手順では、Visual Studio 分離シェル プロジェクト テンプレートを使用して基本的な分離シェル アプリケーションを作成したことを前提とします。 このプロジェクト テンプレートの詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)します。  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio パッケージのプロジェクト テンプレートの場所  
 Visual Studio パッケージのプロジェクト テンプレートは、 **[新しいプロジェクト]** ダイアログの次の 3 つの場所にあります。  
  
1.  **Visual Basic**、 **Extensibility**します。 プロジェクトの既定の言語は Visual Basic です。  
  
2.  **Visual c#**、 **Extensibility**します。 プロジェクトの既定の言語は C# です。  
  
3.  **他のプロジェクト タイプ**、 **Extensibility**します。 プロジェクトの既定の言語は C++ です。  
  
## <a name="adding-a-vspackage"></a>VSPackage の追加  
 VSPackage は、分離シェル アプリケーションを追加できます。 次の手順では、メニュー コマンドを追加する 1 つを作成する方法を示します。  
  
#### <a name="to-add-a-new-vspackage"></a>新しい VSPackage を追加するには  
  
1.  という名前の Visual Studio パッケージ プロジェクトを追加`MenuCommandsPackage`します。  
  
2.  **VSPackage の基本情報**、ウィザードのページ設定**会社名**に`Fabrikam`と**VSPackage 名前**に`FabrikamMenuCommands`します。 **[次へ]** ボタンをクリックします。  
  
3.  次のページで次のように選択します。**メニュー コマンド**選び、**次**します。  
  
4.  次のページで次のように設定します。**コマンド名**に`Fabrikam Command`と**コマンド ID**に`cmdidFabrikamCommand`を選び、 **[次へ]**。  
  
5.  **テスト プロジェクトのオプションを選択** ページで、テストのオプションをオフにして選択し、**完了**ボタンをクリックします。  
  
6.  ShellExtensionsVSIX プロジェクトの source.extension.vsixmanifest ファイルを開きます。  
  
     **資産**セクション VSShellStub.AboutBoxPackage プロジェクトのエントリを含める必要があります。  
  
7.  選択、**新規**ボタンをクリックします。  
  
8.  **新しい資産の追加**ウィンドウで、**型**一覧で、 **Microsoft.VisualStudio.VsPackage**します。  
  
9. **ソース**一覧で、必ず **、現在のソリューションでプロジェクトを**が選択されています。 **プロジェクト**リスト ボックスで、 **MenuCommandsPackage**します。  
  
10. ファイルを保存して閉じます。  
  
11. ソリューションをリビルドし、分離シェルのデバッグを開始します。  
  
12. メニュー バーで、**ツール**メニュー、 **Fabrikam コマンド**します。  
  
     メッセージ ボックスが表示されます。  
  
13. アプリケーションのデバッグを停止します。  
  
## <a name="adding-a-mef-component-part"></a>MEF コンポーネント パーツを追加します。  
 次の手順では、分離シェル アプリケーションに MEF コンポーネント パーツを追加する方法を示します。  
  
#### <a name="to-add-a-mef-component"></a>MEF コンポーネントを追加するには  
  
1.  **新しいプロジェクトの追加**ダイアログ ボックスで、 **Visual c#**、**拡張**を使用して、**エディター余白**テンプレート プロジェクトを追加します。 これに `ShellEditorMargin` という名前を付けます。  
  
2.  ShellExtensionsVSIX プロジェクトでは、コード ビューではなく、デザイン ビューで Source.extension.vsixmanifest ファイルを開きます。  
  
3.  `Asset`セクションで、選択**コンテンツの追加**します。  
  
4.  **新しい資産の追加**ウィンドウで、**型**一覧で、 **Microsoft.VisualStudio.MefComponent**します。  
  
5.  **ソース**一覧で、必ず **、現在のソリューションでプロジェクトを**が選択されています。 **プロジェクト**リスト ボックスで、 **ShellEditorMargin**します。  
  
6.  ファイルを保存して閉じます。  
  
7.  ソリューションをリビルドし、分離シェルのデバッグを開始します。  
  
8.  テキスト ファイルを開きます。  
  
     単語"Hello world!"を含む緑色の余白 テキスト ファイルのウィンドウの下部に表示されます。  
  
9. アプリケーションのデバッグを停止します。  
  
## <a name="adding-a-generic-vsix-project"></a>ジェネリックの VSIX プロジェクトを追加します。  
  
#### <a name="to-add-a-generic-vsix-project"></a>ジェネリックの VSIX プロジェクトに追加するには  
  
1.  **新しいプロジェクトの追加**ダイアログ ボックスで、 **Visual c#**、**拡張**を使用して、 **VSIXProject**テンプレート プロジェクトを追加します。 これに `EmptyVSIX` という名前を付けます。  
  
2.  ShellExtensionsVSIX プロジェクトでは、コード ビューではなく、デザイン ビューで Source.extensions.vsixmanifest ファイルを開きます。  
  
3.  `Assets`セクションで、選択**新規**します。  
  
4.  **新しい資産の追加**ウィンドウで、**型**一覧で、追加するコンテンツの種類を選択します。  
  
5.  **ソース**、ことを確認、**現在のソリューションでプロジェクトを**オプションを選択します。 ボックスの一覧で、VSIX プロジェクトの名前を選択します。  
  
6.  ファイルを保存して閉じます。  
  
7.  このプロジェクトには、コンパイル済みコードが含まれている場合は、アセンブリは、出力に含まれるように、プロジェクトを編集する必要があります。  
  
    1.  VSIX プロジェクトをアンロードし、プロジェクト ファイルを開きます。  
  
    2.  最初の`<PropertyGroup>`ブロックの値を変更`<CopyBuildOutputToOutputDirectory>`に`true`します。  
  
    3.  保存し、プロジェクトの再読み込みします。  
  
8.  ソリューションをビルドして実行します。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)

