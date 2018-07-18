---
title: Visual Studio でのカスタム スタート ページのインストールまたはスタートアップ アイテムの変更
ms.date: 02/01/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start Page
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b5e32a311bcd60542df80518c791b1fbe413a7b2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916608"
---
# <a name="customize-the-start-page-for-visual-studio"></a>Visual Studio のスタート ページをカスタマイズする

Visual Studio の起動時の動作はさまざまな方法でカスタマイズでき、**[プロジェクトを開く]** ダイアログ ボックスを表示するようにしたり、最後に読み込まれたソリューションを開くようにしたりすることができます。 また、カスタム スタート ページを表示することもできます。これは、ツール ウィンドウで実行される Windows Presentation Foundation (WPF) の XAML ページで、Visual Studio 内のコマンドを実行できます。

## <a name="to-change-the-startup-item"></a>スタートアップ アイテムを変更する

1. メニュー バーの **[ツール]**  >  **[オプション]** の順にクリックします。

1. **[環境]** を展開し、**[スタートアップ]** を選びます。

1. **[At startup]\(スタートアップ時\)** リストで、Visual Studio の起動後に表示するアイテムを選択します。

## <a name="to-show-a-custom-start-page"></a>カスタム スタート ページを表示する

Visual Studio SDK を使用して[独自のカスタム スタート ページを作成する](../extensibility/creating-a-custom-start-page.md)か、他のユーザーが既に作成したカスタム スタート ページを利用できます。 たとえば、[Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads) でカスタム スタート ページを検索できます。

カスタム スタート ページをインストールするには、*.vsix* ファイルを開くか、スタート ページ ファイルをコピーしてコンピューターの *%USERPROFILE%\ドキュメント\Visual Studio 2017\StartPages* フォルダーに貼り付けます。

### <a name="to-select-which-custom-start-page-to-display"></a>表示するカスタム スタート ページを選択する

1. メニュー バーの **[ツール]**  >  **[オプション]** の順にクリックします。

1. **[環境]** を展開し、**[スタートアップ]** を選びます。

1. **[スタート ページのカスタマイズ]** の一覧で、使用するページを選択します。

> [!NOTE]
> カスタム スタート ページのエラーによって Visual Studio がクラッシュする場合、セーフ モードで Visual Studio を起動し、既定のスタート ページを使用するように設定します。 「[/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md)」をご覧ください。

## <a name="see-also"></a>関連項目

- [Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)