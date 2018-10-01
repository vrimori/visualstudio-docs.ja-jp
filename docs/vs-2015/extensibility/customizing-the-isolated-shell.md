---
title: 分離シェルのカスタマイズ |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 61cd1d84978baa6f8deb08b2a2cc9327dad543c0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539743"
---
# <a name="customizing-the-isolated-shell"></a>分離シェルのカスタマイズ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[分離シェルのカスタマイズ](https://docs.microsoft.com/visualstudio/extensibility/customizing-the-isolated-shell)します。  
  
Visual Studio のユーザー インターフェイスのさまざまな側面を変更することで、コマンドと特殊化されたアプリケーションに含まれる機能を制限することで、Visual Studio 分離シェル アプリケーションをカスタマイズできます。  
  
## <a name="using-the-applicationpkgdef-file"></a>Application.pkgdef ファイルを使用します。  
 分離シェルのテンプレート ソリューションが含まれています、 *SolutionName*します。次の機能を変更することができます Application.pkgdef ファイル:  
  
##### <a name="the-application-title"></a>アプリケーションのタイトル  
 アプリケーションのタイトルは"AppName"の行の値を変更することで、アプリケーションのタイトル バーに表示される名前を指定することができます、 *SolutionName*します。Application.pkgdef ファイルです。 詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)します。  
  
 アプリケーションのタイトルに現在読み込まれているプロジェクトを表示したくない場合は、"ShowHierarchyRootInTitle"の行の値を変更、 *SolutionName*します。Application.pkgdef のファイルは dword:00000001 から場合は dword:00000000 です。  
  
##### <a name="the-application-icon"></a>アプリケーション アイコン  
 アプリケーションのタイトル バー内のアプリケーション名で表示されるアイコンは、アプリケーションのアイコンをカスタマイズできます。 別のアイコンをアイコンのディレクトリにコピーします。 **ソリューション エクスプ ローラー**、リソース ファイルのフォルダーにアイコンを追加します。 VSShellStub.rc ファイルを開き IDI_STUBPROGRAM の値を新しいアイコンの名前に置き換えます。 詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)します。  
  
##### <a name="the-command-line-logo"></a>コマンド ラインのロゴ  
 コマンド ラインのロゴは、"CommandLineLogo"の行の値を変更することで、コマンドラインから、アプリケーションを起動するときに表示されるテキストをカスタマイズすることができます、 *SolutionName*します。Application.pkgdef ファイルです。 詳細については、次を参照してください[チュートリアル: 基本的な分離シェル アプリケーションを作成する。](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>ユーザー ファイルのサブフォルダーの名前  
 "UserFilesSubFolderName"の行の値を変更することで、アプリケーションがユーザー ファイルの保持フォルダーの名前を変更する*SolutionName*します。Application.pkgdef ファイルです。  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>新しいプロジェクト ダイアログで、ソリューション ツリー ノードのタイトル  
 新しいプロジェクト ダイアログでソリューション ノードのタイトルをカスタマイズするには"NewProjDlgSlnTreeNodeTitle"の行の値を変更することで、 *SolutionName*します。Application.pkgdef ファイルです。  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>新しいプロジェクト ダイアログで、インストール済みのテンプレート ヘッダー  
 新しいプロジェクト ダイアログで、インストール済みのテンプレート ヘッダーを変更するには"NewProjDlgInstalledTemplatesHdr"の行の値を変更することで、 *SolutionName*します。Application.pkgdef ファイルです。  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>既定では、その他のファイルを非表示にするかどうか  
 "HideMiscellaneousFilesByDefault"の行の値を変更することで、既定でその他のファイルを非表示にするかどうかを指定することができます、 *SolutionName*します。Application.pkgdef ファイルです。 その他のファイルを非表示にする値を設定`dword:00000001`、ファイルを表示するには、値を設定および`dword:00000000`します。  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>出力ウィンドウを無効にするかどうか  
 "DisableOutputWindow"の行の値を変更することで、アプリケーションの出力ウィンドウを無効にするかどうかを指定することができます、 *SolutionName*します。Application.pkgdef ファイルです。 出力ウィンドウを無効にする値を設定`dword:00000001`、出力ウィンドウを表示する値を設定および`dword:00000000`します。  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>ドロップされたファイルのメイン ウィンドウを許可するかどうか  
 "AllowsDroppedFilesOnMainWindow"の行の値を変更することで、アプリケーションのメイン ウィンドウにドロップされたファイルを許可するかどうかを指定することができます、 *SolutionName*します。Application.pkgdef ファイルです。 ドロップされたファイルを許可するには、値を設定`dword:00000001`、ドロップされたファイルを禁止する値を設定および`dword:00000000`します。  
  
##### <a name="the-default-search-page"></a>既定の検索ページ  
 "DefaultSearchPage"の行の値を変更することで、web ブラウザー ウィンドウを開いたときに表示されるページには、web ブラウザー ページをカスタマイズすることができます、 *SolutionName*します。Application.pkgdef ファイルです。  
  
##### <a name="the-default-home-page"></a>既定のホーム ページ  
 ホーム ページをカスタマイズするには"DefaultHomePage"の行の値を変更することで、 *SolutionName*します。Application.pkgdef ファイルです。 詳細については、次を参照してください[チュートリアル: 基本的な分離シェル アプリケーションを作成する。](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>ソリューションの概念を非表示にするかどうか  
 "HideSolutionConcept"の行の値を変更することで、アプリケーションでソリューションを非表示にするかどうかを指定することができます、 *SolutionName*します。Application.pkgdef ファイルです。 ソリューションを非表示にする値を設定`dword:00000001`、ソリューションを表示するには、値を設定および`dword:00000000`します。  
  
##### <a name="the-default-debug-engine"></a>既定のデバッグ エンジン  
 "DefaultDebugEngine"の行の値を変更することで、アプリケーションを使用して、デバッグ エンジンを変更することができます、 *SolutionName*します。Application.pkgdef ファイルをデバッグ エンジンの GUID です。  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>ユーザー オプション ファイルのファイル拡張子  
 "UserOptsFileExt"の行の値を変更することで、アプリケーションがユーザー ファイルの保持フォルダーの名前を変更する*SolutionName*します。Application.pkgdef ファイルです。  
  
##### <a name="the-solution-file-extension"></a>ソリューション ファイルの拡張機能  
 "SolutionFileExt"の行の値を変更することで、ソリューション ファイルの使用、拡張機能を変更することができます、 *SolutionName*します。Application.pkgdef ファイルです。  
  
##### <a name="the-default-user-files-folder-root"></a>既定のユーザー ファイル フォルダーのルート  
 アプリケーションのユーザー ファイルのルート フォルダーの名前を変更するには"UserFilesSubFolderName"の行の値を変更することで、 *SolutionName*します。Application.pkgdef ファイルです。  
  
##### <a name="the-solution-file-creator-identifier"></a>ソリューション ファイルの作成者の識別子  
 "SolutionFileCreatorIdentifier"の行の値を変更することで、ソリューション ファイルに使用される id を変更することができます、 *SolutionName*します。Application.pkgdef ファイルです。  
  
##### <a name="the-default-projects-location"></a>既定のプロジェクトの場所  
 既定のプロジェクトの場所の名前を変更するには"DefaultProjectsLocation"の行の値を変更することで、 *SolutionName*します。Application.pkgdef ファイルです。  
  
##### <a name="the-application-localization-package"></a>アプリケーションのローカライズ パッケージ  
 "AppLocalizationPackage"の行の値を変更することで、アプリケーションの使用、ローカライズされたパッケージを変更することができます、 *SolutionName*します。Application.pkgdef ファイルです。  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>タイトルの階層のルートを表示するかどうか  
 "ShowHierarchyRootInTitle"の行の値を変更することで、アプリケーションのタイトル バーで階層のルートを表示するかどうかを指定することができます、 *SolutionName*します。Application.pkgdef ファイルです。 階層のルートを表示するには、値を設定`dword:00000001`、階層のルートを非表示にする値を設定および`dword:00000000`します。  
  
##### <a name="specifying-a-start-page"></a>スタート ページを指定します。  
 カスタム アプリケーションのスタート ページを指定する、 *SolutionName*します。Application.pkgdef ファイルに"DisableStartPage"値を設定する`dword:00000000`、し、 `[$RootKey$\StartPage\Default]` .xaml ファイルの場所に URI を設定します。  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 Applicationcommands.vsct ファイル内の*SolutionName*UI プロジェクトをコメント アウト"No_ShellPkg_startPageCommand"エントリ。  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 .Xaml ファイル、およびの必要な任意のグラフィック ファイルを追加する必要があります、 *SolutionName*プロジェクト。 これらのファイルに実際にコピーする必要があります、 *SolutionName*プロジェクト ディレクトリをその他のディレクトリからは追加されません。  
  
 すべてのファイルに次のように設定します。、**項目の種類**プロパティを**分離シェル ファイル**ファイルにコピーするために、 *$RootFolder$* ディレクトリ。 (設定、**項目の種類**プロパティは、ファイルを右クリックし、選択**プロパティ**します。 このプロパティが見つかります**構成プロパティ**、**全般**)。  
  
 スタート ページをカスタマイズする方法の詳細については、次を参照してください。[スタート ページのカスタマイズ](../ide/customizing-the-start-page-for-visual-studio.md)します。  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>分離シェルの他の要素を使用します。  
 その他のファイルと、アプリケーションをさらにカスタマイズする分離シェルのソリューション テンプレートに含まれているプロジェクトを使用することができます。  
  
##### <a name="enabledisable-visual-studio-packages"></a>Visual Studio パッケージの有効化/無効化  
 *SolutionName*.pkgundef ファイルは、特定のパッケージを除外することで、特定の種類の Visual Studio の機能を無効にすることができます。 たとえば、次のような行があるとします。  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 その他のファイル プロジェクトに表示されるプロジェクト テンプレートのセットから削除、**新しいプロジェクト**ダイアログ。 詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)します。  
  
##### <a name="enabledisable-menu-commands"></a>メニュー コマンドを有効/無効にします。  
 *SolutionName*UI.vsct ファイルには、分離シェルを使用できるすべてのメニュー コマンドのコメント アウトされた一覧が含まれています。 特定のコマンドを無効にするのには、対応する行をコメント解除します。 たとえば、ウィンドウの分割/コメントを無効にするのには、`<Define name="No_SplitCommand"/>`行。 詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)します。  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>スプラッシュ スクリーンで使用されるビットマップ  
 スプラッシュ画面で、"SplashScreenBitmap"の行の値を変更することで、アプリケーションを起動するときに表示されるウィンドウは、使用されるビットマップをカスタマイズすることができます、 *SolutionName*します。Application.pkgdef ファイルです。 詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)します。  
  
##### <a name="the-helpabout-window"></a>ヘルプ、ウィンドウの概要  
 分離シェル テンプレートでは、ヘルプをカスタマイズに使用できる別のプロジェクト]、[アプリケーションのボックスの詳細について。 詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)します。

