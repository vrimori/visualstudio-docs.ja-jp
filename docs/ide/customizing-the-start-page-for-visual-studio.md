---
title: "Visual Studio のスタート ページをカスタマイズする | Microsoft Docs"
ms.custom: 
ms.date: 02/01/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 102091f8214b822a5b6be1c93f913d6ddbcd8d9b
ms.contentlocale: ja-jp
ms.lasthandoff: 05/24/2017

---
# <a name="customize-the-start-page-for-visual-studio"></a>Visual Studio のスタート ページをカスタマイズする
Visual Studio のスタート ページは、既定のさまざまな方法でカスタマイズできます。**[プロジェクトを開く]** ダイアログ ボックスを表示することも、最後に読み込まれたソリューションを開くこともできます。 また、カスタム スタート ページを表示することもできます。これは、ツール ウィンドウで実行される Windows Presentation Foundation (WPF) の XAML ページで、Visual Studio 内のコマンドを実行できます。  

## <a name="customize-the-default-start-page"></a>既定のスタート ページをカスタマイズする  

1.  メニュー バーの **[ツール]**、 **[オプション]**の順にクリックします。  

2.  **[環境]** を展開し、**[スタートアップ]** を選びます。  

3.  **[スタートアップ時]** の一覧で、カスタマイズ対象の項目を選びます。  

## <a name="show-a-custom-start-page"></a>カスタム スタート ページの表示  

1.  次のいずれかの方法でカスタム スタート ページをインストールします。  

    -   [Visual Studio ギャラリー](http://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=start%20page)、別の Web サイト、またはローカル イントラネットのページからインストールします。  

        カスタム スタート ページを含む .vsix ファイルを開くか、スタート ページ ファイルをコピーしてコンピューターの **%USERPROFILE% \My Documents\Visual Studio 2017\StartPages** フォルダーに貼り付けます。  

    -   Visual Studio SDK をインストールしている場合は独自のスタート ページを作成できます。  

         「[カスタム スタート ページを作成する](../extensibility/creating-a-custom-start-page.md)」をご覧ください。  

2.  メニュー バーの **[ツール]**、 **[オプション]**の順にクリックします。  

3.  **[環境]** を展開し、**[スタートアップ]** を選びます。  

4.  **[スタート ページのカスタマイズ]** の一覧で、使用するページを選択します。  

> [!NOTE]
>  カスタム スタート ページのエラーによって Visual Studio がクラッシュする場合、セーフ モードで Visual Studio を起動し、既定のスタート ページを使用するように設定します。 「[/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md)」をご覧ください。  

## <a name="see-also"></a>関連項目  
 [Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)   

