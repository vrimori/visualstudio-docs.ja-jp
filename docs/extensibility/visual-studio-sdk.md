---
title: "Visual Studio SDK |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 56
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
ms.sourcegitcommit: 477f57bbca9c49e7d7d13155fc1f6e55ee4667a8
ms.openlocfilehash: efc5a2722757229057a91f5e3a6c2ad3681f5a89
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Visual Studio SDK を使用すると、Visual Studio の機能を拡張したり、新機能を Visual Studio に統合できます。 他のユーザーだけでなく、Visual Studio ギャラリーに拡張機能を配布することができます。 Visual Studio を拡張する方法の一部を次に示します。  
  
-   IDE にコマンド、ボタン、メニューのおよびその他の UI 要素を追加します。  
  
-   ツール ウィンドウの新しい機能についての追加します。  
  
-   特定の言語の IntelliSense を拡張したり、新しいプログラミング言語の IntelliSense を提供  
  
-   電球を使用して、優れたコードを記述のヒントと開発者を支援する提案を提供するには  
  
-   新しい言語のサポートを有効にします。  
  
-   カスタムのプロジェクトの種類を追加します。  
  
-   非常に多くの開発者が Visual Studio ギャラリーから  
  
 詳細については、これらの機能に関するはずの前に Visual Studio 拡張機能を作成してない場合[Visual Studio 拡張機能の開発を開始して](../extensibility/starting-to-develop-visual-studio-extensions.md)します。  
  
## <a name="installing-the-visual-studio-sdk"></a>Visual Studio SDK をインストールします。  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>Visual Studio 2015 SDK の新機能します。  
 Visual Studio SDK は、電球メニュー コマンド、ツール ウィンドウおよびエディターの拡張機能の VSIX パッケージを使用して作成するための新しいプロジェクト項目など、一部の新機能です。 詳細については、次を参照してください。 [what ' s New in Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md)します。  
  
## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio ユーザー エクスペリエンス ガイドライン  
 拡張機能の UI を設計するために役立つヒントを取得[Visual Studio のユーザー エクスペリエンス ガイドライン](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)します。  
  
 高 DPI デバイスに美しく表示拡張機能を作成する方法を確認できます、[アドレス指定の DPI 問題](../extensibility/addressing-dpi-issues2.md)トピックです。  
  
 利用、[イメージ サービスとカタログ](../extensibility/image-service-and-catalog.md)優れたイメージの管理と高 DPI とテーマのサポート。  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>検索および既存の Visual Studio 拡張機能をインストールします。  
 Visual Studio 拡張機能を見つけることができます、**拡張機能と更新プログラム**ダイアログ ボックスで、**ツール**メニュー。 詳細については、次を参照してください。 [Visual Studio 拡張機能の使用を検索および](../ide/finding-and-using-visual-studio-extensions.md)です。 内の拡張機能を検索することも、 [Visual Studio ギャラリー](https://visualstudiogallery.msdn.microsoft.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Visual Studio SDK のリファレンス  
 Visual Studio SDK の API リファレンスを検索できます[Visual Studio SDK のリファレンス](../extensibility/visual-studio-sdk-reference.md)します。  
  
## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK のサンプル  
 GitHub での VS SDK 拡張機能のオープン ソースの例を検索できます[Visual Studio のサンプル](https://aka.ms/vs2015sdksamples)します。 この GitHub リポジトリには、Visual Studio でのさまざまな拡張機能を説明するサンプルが含まれています。  
  
## <a name="other-visual-studio-sdk-resources"></a>その他の Visual Studio SDK のリソース  
 VSSDK について質問がある場合または拡張機能の開発経験を共有する場合は場合、使用して、 [Visual Studio 機能拡張フォーラム](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)または[ExtendVS グループ チャット](https://gitter.im/Microsoft/extendvs)します。  
  
 詳細については 『 を見つけることができます、 [VSX Arcana ブログ](http://blogs.msdn.com/b/vsx/)および Microsoft Mvp によって書き込まれたブログの番号。  
  
-   [お気に入りの Visual Studio 拡張機能](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Visual Studio 拡張機能](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Visual Studio の拡張](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>関連項目  
 [メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [方法: Visual Studio 2015 への機能拡張プロジェクトの移行](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [FAQ: アドインを VSPackage 拡張機能に変換します。](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [マネージ コード内の複数のスレッドを管理します。](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [拡張メニューとコマンド](../extensibility/extending-menus-and-commands.md)   
 [ツールバーにコマンドを追加します。](../extensibility/adding-commands-to-toolbars.md)   
 [拡張とカスタマイズ ツール ウィンドウ](../extensibility/extending-and-customizing-tool-windows.md)   
 [エディターと言語サービスの拡張機能](../extensibility/editor-and-language-service-extensions.md)   
 [プロジェクトの拡張](../extensibility/extending-projects.md)   
 [ユーザー設定の拡張とオプション](../extensibility/extending-user-settings-and-options.md)   
 [カスタムのプロジェクトおよび項目テンプレートを作成します。](../extensibility/creating-custom-project-and-item-templates.md)   
 [プロパティと [プロパティ] ウィンドウの拡張](../extensibility/extending-properties-and-the-property-window.md)   
 [Visual Studio の他の部分を拡張します。](../extensibility/extending-other-parts-of-visual-studio.md)   
 [使用して、サービスを提供します。](../extensibility/using-and-providing-services.md)   
 [Vspackage を管理します。](../extensibility/managing-vspackages.md)   
 [Visual Studio シェルの分離](../extensibility/visual-studio-isolated-shell.md)   
 [Visual Studio 拡張機能を配布](../extensibility/shipping-visual-studio-extensions.md)   
 [Visual Studio SDK 内](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Visual Studio SDK のサポート](../extensibility/support-for-the-visual-studio-sdk.md)   
 [アーカイブ](../extensibility/archive.md)   
 [Visual Studio SDK のリファレンス](../extensibility/visual-studio-sdk-reference.md)
