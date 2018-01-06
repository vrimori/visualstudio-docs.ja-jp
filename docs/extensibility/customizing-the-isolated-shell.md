---
redirect_url: shell/customizing-the-isolated-shell
title: "分離シェルをカスタマイズする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e02d93e966f676e0933b866cc8e74bfdd011231f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-the-isolated-shell"></a>分離シェルのカスタマイズ
Visual Studio ユーザー インターフェイスのさまざまな側面を変更することで、コマンドと特殊化されたアプリケーションに含まれる機能を制限することで、Visual Studio 分離シェル アプリケーションをカスタマイズすることができます。  
  
## <a name="using-the-applicationpkgdef-file"></a>Application.pkgdef ファイルを使用します。  
 分離シェル テンプレート ソリューションに含まれて、 *SolutionName*です。次の機能を変更することができます Application.pkgdef ファイル:  
  
##### <a name="the-application-title"></a>アプリケーションのタイトル  
 "AppName"の行の値を変更することによって、アプリケーションのタイトル バーに表示される名前になっているアプリケーション タイトルをカスタマイズすることができます、 *SolutionName*です。Application.pkgdef ファイルです。 詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)です。  
  
 アプリケーションのタイトルに現在読み込まれているプロジェクトを表示したくない場合は、"ShowHierarchyRootInTitle"の行の値を変更、 *SolutionName*です。Application.pkgdef のファイルは dword:00000001 を dword:00000000 です。  
  
##### <a name="the-application-icon"></a>アプリケーション アイコン  
 アプリケーションのタイトル バー内のアプリケーション名で表示されるアイコンは、アプリケーションのアイコンをカスタマイズすることができます。 別のアイコンをアイコンのディレクトリにコピーします。 **ソリューション エクスプ ローラー**、リソース ファイル フォルダーにアイコンを追加します。 VSShellStub.rc ファイルを開き IDI_STUBPROGRAM の値を新しいアイコンの名前に置き換えます。 詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)です。  
  
##### <a name="the-command-line-logo"></a>コマンド ラインのロゴ  
 "CommandLineLogo"の行の値を変更することによって、アプリケーションが、コマンドラインから開始されたときに表示されるテキストは、コマンド ラインのロゴをカスタマイズすることができます、 *SolutionName*です。Application.pkgdef ファイルです。 詳細については、次を参照してください[チュートリアル: 基本的な分離シェル アプリケーションを作成する。](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>ユーザー ファイルのサブフォルダーの名前  
 "UserFilesSubFolderName"の行の値を変更することによって、アプリケーションがユーザー ファイルの保持フォルダーの名前を変更することができます*SolutionName*です。Application.pkgdef ファイルです。  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>[新しいプロジェクト] ダイアログ ボックスのソリューション ツリー ノードのタイトル  
 新しいプロジェクト ダイアログでソリューション ノードのタイトルをカスタマイズするには"NewProjDlgSlnTreeNodeTitle"の行の値を変更することによって、 *SolutionName*です。Application.pkgdef ファイルです。  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>新しいプロジェクト ダイアログで、インストール済みテンプレート ヘッダー  
 新しいプロジェクト ダイアログで、インストール済みテンプレート ヘッダーを変更するには"NewProjDlgInstalledTemplatesHdr"の行の値を変更することによって、 *SolutionName*です。Application.pkgdef ファイルです。  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>既定では、その他のファイルを非表示にするかどうか  
 "HideMiscellaneousFilesByDefault"の行の値を変更することで、既定ではその他のファイルを非表示にするかどうかを指定することができます、 *SolutionName*です。Application.pkgdef ファイルです。 その他のファイルを非表示には、この値を設定します。 `dword:00000001`、ファイルを表示するには、値を設定および`dword:00000000`です。  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>出力ウィンドウを無効にするかどうか  
 "DisableOutputWindow"の行の値を変更することによって、アプリケーションの出力ウィンドウを無効にするかどうかを指定することができます、 *SolutionName*です。Application.pkgdef ファイルです。 出力ウィンドウを無効にするには、この値を設定`dword:00000001`、出力ウィンドウを表示するには、この値を設定および`dword:00000000`です。  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>メイン ウィンドウでファイルの削除を許可するかどうか  
 "AllowsDroppedFilesOnMainWindow"の行の値を変更することによって、アプリケーションでのメイン ウィンドウでファイルの削除を許可するかどうかを指定することができます、 *SolutionName*です。Application.pkgdef ファイルです。 ファイルの削除を許可するには、この値を設定`dword:00000001`、ドロップされたファイルが行われないよう、値を設定および`dword:00000000`です。  
  
##### <a name="the-default-search-page"></a>既定の検索ページ  
 これは"DefaultSearchPage"の行の値を変更することによって、web ブラウザーのウィンドウを開いたときに表示されるページ、web ブラウザー ページをカスタマイズすることができます、 *SolutionName*です。Application.pkgdef ファイルです。  
  
##### <a name="the-default-home-page"></a>既定のホーム ページ  
 "DefaultHomePage"の行の値を変更することで、ホーム ページをカスタマイズすることができます、 *SolutionName*です。Application.pkgdef ファイルです。 詳細については、次を参照してください[チュートリアル: 基本的な分離シェル アプリケーションを作成する。](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>ソリューションの概念を非表示にするかどうか  
 "HideSolutionConcept"の行の値を変更することによって、アプリケーションで、ソリューションを非表示にするかどうかを指定することができます、 *SolutionName*です。Application.pkgdef ファイルです。 ソリューションを非表示には、この値を設定します。 `dword:00000001`、ソリューションを表示するには、値を設定および`dword:00000000`です。  
  
##### <a name="the-default-debug-engine"></a>既定のデバッグ エンジン  
 "DefaultDebugEngine"の行の値を変更することによって、アプリケーションを使用して、デバッグ エンジンを変更することができます、 *SolutionName*です。デバッグ エンジンの GUID を Application.pkgdef ファイルです。  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>ユーザー オプション ファイルのファイル拡張子  
 "UserOptsFileExt"の行の値を変更することによって、アプリケーションがユーザー ファイルの保持フォルダーの名前を変更することができます*SolutionName*です。Application.pkgdef ファイルです。  
  
##### <a name="the-solution-file-extension"></a>ソリューション ファイルの拡張子  
 "SolutionFileExt"の行の値を変更することで、ソリューション ファイルを使用する拡張機能を変更することができます、 *SolutionName*です。Application.pkgdef ファイルです。  
  
##### <a name="the-default-user-files-folder-root"></a>既定のユーザー ファイル フォルダーのルート  
 アプリケーションのユーザー ファイルのルート フォルダーの名前を変更するには"UserFilesSubFolderName"の行の値を変更することによって、 *SolutionName*です。Application.pkgdef ファイルです。  
  
##### <a name="the-solution-file-creator-identifier"></a>ソリューション ファイル作成者 id  
 "SolutionFileCreatorIdentifier"の行の値を変更することで、ソリューション ファイルを使用する識別子を変更することができます、 *SolutionName*です。Application.pkgdef ファイルです。  
  
##### <a name="the-default-projects-location"></a>既定のプロジェクトの場所  
 既定のプロジェクトの場所の名前を変更するには"DefaultProjectsLocation"の行の値を変更することによって、 *SolutionName*です。Application.pkgdef ファイルです。  
  
##### <a name="the-application-localization-package"></a>アプリケーションのローカライズ パッケージ  
 "AppLocalizationPackage"の行の値を変更することによって、アプリケーションの使用、ローカライズされたパッケージを変更することができます、 *SolutionName*です。Application.pkgdef ファイルです。  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>タイトルに階層のルートを表示するかどうか  
 "ShowHierarchyRootInTitle"の行の値を変更することによって、アプリケーションのタイトル バーに、階層のルートを表示するかどうかを指定することができます、 *SolutionName*です。Application.pkgdef ファイルです。 階層のルートを表示するには、値を設定`dword:00000001`、階層のルートを非表示にする値を設定および`dword:00000000`です。  
  
##### <a name="specifying-a-start-page"></a>スタート ページを指定します。  
 カスタム アプリケーションのスタート ページを指定する、 *SolutionName*です。Application.pkgdef ファイルでは、値を設定"DisableStartPage" `dword:00000000`、し、 `[$RootKey$\StartPage\Default]` .xaml ファイルの場所に URI を設定します。  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 Applicationcommands.vsct ファイルで、 *SolutionName*UI プロジェクトをコメント アウト"No_ShellPkg_startPageCommand"エントリ。  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 .Xaml ファイルとへの必要なすべてのグラフィックス ファイルを追加する必要があります、 *SolutionName*プロジェクト。 これらのファイルに実際にコピーする必要があります、 *SolutionName*プロジェクト ディレクトリをその他のディレクトリからは追加されません。  
  
 すべてのファイルの設定、**項目の種類**プロパティを**分離シェル ファイル**にコピーするファイルの順序で、 *$RootFolder$*ディレクトリ。 (設定、**項目の種類**プロパティをファイルを右クリックし、クリックして**プロパティ**です。 このプロパティは、**構成プロパティ**、**全般**)。  
  
 スタート ページをカスタマイズする方法の詳細については、次を参照してください。[スタート ページのカスタマイズ](../ide/customizing-the-start-page-for-visual-studio.md)です。  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>分離シェルの他の要素を使用します。  
 その他のファイルと、アプリケーションをさらにカスタマイズする、分離シェル ソリューション テンプレートに含まれているプロジェクトを使用することができます。  
  
##### <a name="enabledisable-visual-studio-packages"></a>Visual Studio パッケージを有効/無効にします。  
 *SolutionName*.pkgundef ファイルでは、特定のパッケージを除外することで特定の種類の Visual Studio の機能を無効にすることができます。 たとえば、次のような行があるとします。  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 その他のファイル プロジェクトに表示されるプロジェクト テンプレートのセットから削除、**新しいプロジェクト**ダイアログ。 詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)です。  
  
##### <a name="enabledisable-menu-commands"></a>メニュー コマンドを有効/無効にします。  
 *SolutionName*UI.vsct ファイルには、分離シェルを使用できるすべてのメニュー コマンドのコメント アウトされた一覧が含まれています。 指定されたコマンドを無効にするには、対応する行をコメントを解除します。 たとえばに、ウィンドウの分割/コメントを無効にするには、コメントを解除、`<Define name="No_SplitCommand"/>`行です。 詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)です。  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>スプラッシュ スクリーンに使用されるビットマップ  
 スプラッシュ画面で、"SplashScreenBitmap"の行の値を変更することによって、アプリケーションが開始されたときに表示されるウィンドウで使用されるビットマップをカスタマイズすることができます、 *SolutionName*です。Application.pkgdef ファイルです。 詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)です。  
  
##### <a name="the-helpabout-window"></a>ヘルプ/アバウト ウィンドウ  
 分離シェル テンプレートは、ヘルプをカスタマイズに使用できる個別のプロジェクト/アプリケーションのボックスの詳細。 詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)です。