---
title: Visual Studio SDK |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 57
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e64506ca544dd3811864358f9c928f6893dc8448
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758969"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK を使用して、Visual Studio の機能を拡張するかを Visual Studio の新機能を統合するのに役立ちます。 他のユーザーのほか、Visual Studio ギャラリーには、拡張機能を配布することができます。 Visual Studio を拡張する方法の一部を次に示します。  
  
- IDE にコマンド、ボタン、メニューのおよびその他の UI 要素を追加します。  
  
- ツール ウィンドウの新しい機能を追加します。  
  
- 特定の言語の IntelliSense の拡張または新しいプログラミング言語に対して IntelliSense を提供  
  
- 電球を使用して、優れたコードを記述のヒントと開発者に役立つ提案を提供するには  
  
- 新しい言語のサポートを有効にします。  
  
- カスタム プロジェクトの種類を追加します。  
  
- Visual Studio ギャラリーを使用して開発者の何百万します。  
  
  前に Visual Studio 拡張機能を初めて作成する場合とでこれらの機能についての詳細についてを検索する必要があります[Visual Studio 拡張機能の開発を開始しています](../extensibility/starting-to-develop-visual-studio-extensions.md)します。  
  
## <a name="installing-the-visual-studio-sdk"></a>Visual Studio SDK をインストールします。  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>新機能については、Visual Studio 2015 SDK です。  
 Visual Studio SDK には、電球メニュー コマンド、ツール ウィンドウ、およびエディターの拡張機能の VSIX パッケージを使用して作成するための新しいプロジェクト項目など、一部の新機能があります。 詳細については、次を参照してください。 [、Visual Studio 2015 SDK の新](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md)します。  
  
## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio ユーザー エクスペリエンス ガイドライン  
 拡張機能の UI を設計するための便利なヒントを取得[Visual Studio ユーザー エクスペリエンス ガイドライン](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)します。  
  
 高 DPI デバイスに美しく表示拡張機能を作成する方法を確認できます、 [DPI 問題の対処](../extensibility/addressing-dpi-issues2.md)トピック。  
  
 利用、[イメージ サービスとカタログ](../extensibility/image-service-and-catalog.md)イメージの管理や高 DPI とテーマのサポート。  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>検索して、既存の Visual Studio 拡張機能のインストール  
 Visual Studio 拡張機能を見つけることができます、**拡張機能と更新**ダイアログで、**ツール**メニュー。 詳細については、「[Visual Studio 拡張機能の検索と使用](../ide/finding-and-using-visual-studio-extensions.md)」を参照してください。 拡張機能を検索することも、 [Visual Studio ギャラリー](https://visualstudiogallery.msdn.microsoft.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Visual Studio SDK のリファレンス  
 Visual Studio SDK の API リファレンスに見つかります[Visual Studio SDK リファレンス](../extensibility/visual-studio-sdk-reference.md)します。  
  
## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK のサンプル  
 Github の VS SDK 拡張機能のオープン ソースの例が見つかります[Visual Studio のサンプル](https://aka.ms/vs2015sdksamples)します。 この GitHub リポジトリには、Visual Studio のさまざまな拡張機能を示すサンプルが含まれています。  
  
## <a name="other-visual-studio-sdk-resources"></a>その他の Visual Studio SDK のリソース  
 使用することができます、VSSDK について質問があるか、拡張機能の開発経験を共有する場合、 [Visual Studio 機能拡張フォーラム](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)または[ExtendVS グループ チャット](https://gitter.im/Microsoft/extendvs)します。  
  
 詳細を確認することができます、 [VSX Arcana ブログ](http://blogs.msdn.com/b/vsx/)および Microsoft Mvp によって作成されたブログの番号。  
  
-   [お気に入りの Visual Studio 拡張機能](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Visual Studio 機能拡張](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Visual Studio の拡張](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>関連項目  
 [メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [方法: 機能拡張プロジェクトを Visual Studio 2015 に移行](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [FAQ: アドインを VSPackage 拡張機能に変換します。](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [マネージ コード内の複数のスレッドを管理します。](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [拡張メニューとコマンド](../extensibility/extending-menus-and-commands.md)   
 [ツールバーにコマンドを追加します。](../extensibility/adding-commands-to-toolbars.md)   
 [拡張とカスタマイズ ツール Windows](../extensibility/extending-and-customizing-tool-windows.md)   
 [エディターと言語サービス拡張機能](../extensibility/editor-and-language-service-extensions.md)   
 [プロジェクトの拡張](../extensibility/extending-projects.md)   
 [拡張ユーザー設定とオプション](../extensibility/extending-user-settings-and-options.md)   
 [カスタム プロジェクトと項目テンプレートの作成](../extensibility/creating-custom-project-and-item-templates.md)   
 [プロパティと、[プロパティ] ウィンドウの拡張](../extensibility/extending-properties-and-the-property-window.md)   
 [Visual Studio の他の部分を拡張します。](../extensibility/extending-other-parts-of-visual-studio.md)   
 [使用して、サービスを提供します。](../extensibility/using-and-providing-services.md)   
 [接続済みサービスを拡張します。](../extensibility/extending-connected-services.md)   
 [Vspackage の管理](../extensibility/managing-vspackages.md)   
 [Visual Studio 分離シェル](../extensibility/visual-studio-isolated-shell.md)   
 [Visual Studio 拡張機能を配布](../extensibility/shipping-visual-studio-extensions.md)   
 [Visual Studio SDK の内部](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Visual Studio SDK のサポート](../extensibility/support-for-the-visual-studio-sdk.md)   
 [アーカイブ](../extensibility/archive.md)   
 [Visual Studio SDK のリファレンス](../extensibility/visual-studio-sdk-reference.md)

