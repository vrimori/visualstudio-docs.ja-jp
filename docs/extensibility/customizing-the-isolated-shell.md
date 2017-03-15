---
title: "分離シェルをカスタマイズする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 15
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
ms.openlocfilehash: f36bfb81f311db0f49d399f86007f10d618b7ba3
ms.lasthandoff: 02/22/2017

---
# <a name="customizing-the-isolated-shell"></a>分離シェルをカスタマイズします。
Visual Studio ユーザー インターフェイスのさまざまな側面を変更することで、コマンドと特殊なアプリケーションに含まれる機能を制限することで、分離された Visual Studio シェル アプリケーションをカスタマイズできます。  
  
## <a name="using-the-applicationpkgdef-file"></a>Application.pkgdef ファイルを使用します。  
 分離シェル テンプレート ソリューションには、 *SolutionName*します。では、次の機能を変更する Application.pkgdef ファイル:  
  
##### <a name="the-application-title"></a>アプリケーションのタイトル  
 アプリケーションのタイトルは、"AppName"の行の値を変更することで、アプリケーションのタイトル バーに表示される名前を指定することができます、 *SolutionName*します。Application.pkgdef ファイルです。 詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)です。  
  
 アプリケーションのタイトルに現在読み込まれているプロジェクトを表示したくない場合は、"ShowHierarchyRootInTitle"の行の値を変更、 *SolutionName*します。Application.pkgdef のファイルは、dword:00000001 の場合は dword:00000000 です。  
  
##### <a name="the-application-icon"></a>[アプリケーション] アイコン  
 アプリケーションのタイトル バー内のアプリケーション名が表示されるアイコンは、アプリケーションのアイコンをカスタマイズできます。 別のアイコンをアイコン ディレクトリにコピーします。 **ソリューション エクスプ ローラー**、リソース ファイル フォルダーにアイコンを追加します。 VSShellStub.rc ファイルを開き IDI_STUBPROGRAM の値を新しいアイコンの名前に置き換えます。 詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)です。  
  
##### <a name="the-command-line-logo"></a>コマンド ラインのロゴ  
 コマンド ラインのロゴは、"CommandLineLogo"の行の値を変更して、コマンドラインから、アプリケーションを起動するときに表示されるテキストをカスタマイズすることができます、 *SolutionName*します。Application.pkgdef ファイルです。 詳細については、次を参照してください[チュートリアル: 基本的な分離シェル アプリケーションを作成する。](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>ユーザー ファイルのサブフォルダーの名前  
 "UserFilesSubFolderName"の行の値を変更することで、アプリケーションがユーザー ファイルの保持フォルダーの名前を変更する*SolutionName*します。Application.pkgdef ファイルです。  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>新しいプロジェクト ダイアログで、ソリューションのツリー ノードのタイトル  
 新しいプロジェクト ダイアログでソリューション ノードのタイトルをカスタマイズするには"NewProjDlgSlnTreeNodeTitle"の行の値を変更することで、 *SolutionName*します。Application.pkgdef ファイルです。  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>新しいプロジェクト ダイアログで、インストールされているテンプレート ヘッダー  
 新しいプロジェクト ダイアログでインストールされたテンプレートのヘッダーを変更するには"NewProjDlgInstalledTemplatesHdr"の行の値を変更することで、 *SolutionName*します。Application.pkgdef ファイルです。  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>既定では、その他のファイルを非表示にするかどうか  
 "HideMiscellaneousFilesByDefault"の行の値を変更することで、既定でその他のファイルを非表示にするかどうかを指定することができます、 *SolutionName*します。Application.pkgdef ファイルです。 その他のファイルを非表示には、値を設定します。 `dword:00000001`、ファイルを表示するには、値を設定および`dword:00000000`です。  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>[出力] ウィンドウを無効にするかどうか  
 "DisableOutputWindow"の行の値を変更することで、アプリケーションの出力ウィンドウを無効にするかどうかを指定することができます、 *SolutionName*します。Application.pkgdef ファイルです。 [出力] ウィンドウを無効にするには、値を設定`dword:00000001`、出力ウィンドウを表示するには、値を設定および`dword:00000000`です。  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>メイン ウィンドウで削除されたファイルを許可するかどうか  
 "AllowsDroppedFilesOnMainWindow"の行の値を変更することで、アプリケーションのメイン ウィンドウにドロップされたファイルを許可するかどうかを指定することができます、 *SolutionName*します。Application.pkgdef ファイルです。 ドロップされたファイルを許可するように値を設定`dword:00000001`、ドロップされたファイルをしない場合に、値を設定および`dword:00000000`です。  
  
##### <a name="the-default-search-page"></a>既定の検索ページ  
 これは"DefaultSearchPage"の行の値を変更することで、web ブラウザーのウィンドウを開いたときに表示されるページ、web ブラウザー ページをカスタマイズすることができます、 *SolutionName*します。Application.pkgdef ファイルです。  
  
##### <a name="the-default-home-page"></a>既定のホーム ページ  
 ホーム ページをカスタマイズするには"DefaultHomePage"の行の値を変更することで、 *SolutionName*します。Application.pkgdef ファイルです。 詳細については、次を参照してください[チュートリアル: 基本的な分離シェル アプリケーションを作成する。](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>ソリューションの概念を非表示にするかどうか  
 "HideSolutionConcept"の行の値を変更することで、アプリケーションのソリューションを非表示にするかどうかを指定することができます、 *SolutionName*します。Application.pkgdef ファイルです。 ソリューションを非表示には、値を設定します。 `dword:00000001`、ソリューションを示す値を設定および`dword:00000000`です。  
  
##### <a name="the-default-debug-engine"></a>既定のデバッグ エンジン  
 "DefaultDebugEngine"の行の値を変更することで、アプリケーションを使用してデバッグ エンジンを変更することができます、 *SolutionName*します。デバッグ エンジンの GUID へ Application.pkgdef ファイルです。  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>ユーザー オプション ファイルのファイル拡張子  
 "UserOptsFileExt"の行の値を変更することで、アプリケーションがユーザー ファイルの保持フォルダーの名前を変更する*SolutionName*します。Application.pkgdef ファイルです。  
  
##### <a name="the-solution-file-extension"></a>ソリューション ファイルの拡張子  
 "SolutionFileExt"の行の値を変更することで、ソリューション ファイルを使用する拡張機能を変更することができます、 *SolutionName*します。Application.pkgdef ファイルです。  
  
##### <a name="the-default-user-files-folder-root"></a>既定のユーザー ファイル フォルダーのルート  
 アプリケーションのユーザー ファイルのルート フォルダーの名前を変更するには"UserFilesSubFolderName"の行の値を変更することで、 *SolutionName*します。Application.pkgdef ファイルです。  
  
##### <a name="the-solution-file-creator-identifier"></a>ソリューション ファイルの作成者の識別子  
 "SolutionFileCreatorIdentifier"の行の値を変更することで、ソリューション ファイルに使用される識別子を変更することができます、 *SolutionName*します。Application.pkgdef ファイルです。  
  
##### <a name="the-default-projects-location"></a>既定のプロジェクトの場所  
 既定のプロジェクトの場所の名前を変更するには"DefaultProjectsLocation"の行の値を変更することで、 *SolutionName*します。Application.pkgdef ファイルです。  
  
##### <a name="the-application-localization-package"></a>アプリケーションのローカライズ パッケージ  
 "AppLocalizationPackage"の行の値を変更することで、アプリケーションのために使用するローカライズ パッケージを変更できる、 *SolutionName*します。Application.pkgdef ファイルです。  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>タイトルに階層のルートを表示するかどうか  
 "ShowHierarchyRootInTitle"の行の値を変更することで、アプリケーションのタイトル バーで階層のルートを表示するかどうかを指定することができます、 *SolutionName*します。Application.pkgdef ファイルです。 階層のルートを表示するには、値を設定`dword:00000001`、階層のルートを非表示にするには、値を設定および`dword:00000000`です。  
  
##### <a name="specifying-a-start-page"></a>スタート ページを指定します。  
 カスタム アプリケーションのスタート ページを指定する、 *SolutionName*します。Application.pkgdef ファイルでは、"DisableStartPage"の値を設定`dword:00000000`、および  `[$RootKey$\StartPage\Default]` .xaml ファイルの場所に URI を設定します。  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 Applicationcommands.vsct ファイルで、 *SolutionName*UI プロジェクトを"No_ShellPkg_startPageCommand"エントリをコメント解除します。  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 .Xaml ファイルおよびへの必要な任意のグラフィック ファイルを追加する必要があります、 *SolutionName*プロジェクトです。 これらのファイルを実際にコピーする必要があります、 *SolutionName*プロジェクト ディレクトリをその他のディレクトリからは追加されません。  
  
 すべてのファイルで設定、**項目の種類**プロパティを**分離シェル ファイル**ファイルにコピーするために、 *$RootFolder$*ディレクトリ。 (設定する、**項目の種類**プロパティをファイルを右クリックし、クリックして**プロパティ**します。 このプロパティは、**構成プロパティ**、**全般**)。  
  
 スタート ページをカスタマイズする方法の詳細については、次を参照してください。[スタート ページをカスタマイズする](../ide/customizing-the-start-page-for-visual-studio.md)です。  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>分離シェルの他の要素を使用  
 その他のファイルとさらに、アプリケーションをカスタマイズする分離シェル ソリューション テンプレートに含まれているプロジェクトを使用することができます。  
  
##### <a name="enabledisable-visual-studio-packages"></a>Visual Studio の パッケージの有効化/無効化  
 *SolutionName*.pkgundef ファイルでは、特定のパッケージを除外することで特定の種類の Visual Studio の機能を無効にすることができます。 たとえば、次のような行があるとします。  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 その他のファイル プロジェクトをプロジェクトに表示されるテンプレートのセットから削除、**新しいプロジェクト**ダイアログ。 詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)です。  
  
##### <a name="enabledisable-menu-commands"></a>メニュー コマンドの有効化/無効化  
 *SolutionName*UI.vsct ファイルには、分離シェルを使用可能なすべてのメニュー コマンドのコメント アウトされた一覧が含まれています。 指定されたコマンドを無効にするのには、対応する行をコメント解除します。 たとえば、ウィンドウの分割/コメントを無効にするをコメント解除、`<Define name="No_SplitCommand"/>`行です。 詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)です。  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>スプラッシュ スクリーンに使用されるビットマップ  
 スプラッシュ画面で、"SplashScreenBitmap"の行の値を変更することで、アプリケーションが起動するときに表示されるウィンドウは、使用されるビットマップをカスタマイズすることができます、 *SolutionName*します。Application.pkgdef ファイルです。 詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)です。  
  
##### <a name="the-helpabout-window"></a>ヘルプ/ ウィンドウについて  
 分離シェル テンプレートは、ヘルプをカスタマイズに使用できる別のプロジェクト]、[アプリケーションのボックスの詳細。 詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)です。
