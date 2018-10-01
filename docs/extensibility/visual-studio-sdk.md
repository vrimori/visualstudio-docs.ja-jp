---
title: Visual Studio SDK |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 794d1bae562bf107d9986a132a44d4fa95aec20d
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495818"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Visual Studio SDK を使用して、Visual Studio の機能を拡張するかを Visual Studio の新機能を統合するのに役立ちます。 他のユーザーのほか、Visual Studio Marketplace には、拡張機能を配布することができます。 Visual Studio を拡張する方法の一部を次に示します。  
  
-   IDE にコマンド、ボタン、メニューのおよびその他の UI 要素を追加します。  
  
-   ツール ウィンドウの新しい機能を追加します。  
  
-   特定の言語の IntelliSense の拡張または新しいプログラミング言語に対して IntelliSense を提供  
  
-   電球を使用して、優れたコードを記述のヒントと開発者に役立つ提案を提供するには  
  
-   新しい言語のサポートを有効にします。  
  
-   カスタム プロジェクトの種類を追加します。  
  
-   Visual Studio Marketplace での開発者の何百万します。  
  
 前に Visual Studio 拡張機能を初めて作成する場合とでこれらの機能についての詳細についてを検索する必要があります[Visual Studio 拡張機能の開発を始める](../extensibility/starting-to-develop-visual-studio-extensions.md)します。  
  
## <a name="install-the-visual-studio-sdk"></a>Visual Studio SDK のインストール  
 Visual Studio SDK は、Visual Studio セットアップで省略可能な機能です。 また、後から VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)します。  
  
## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>新機能については、Visual Studio 2017 SDK です。  
 Visual Studio SDK が、一部の新機能など、VSIX v3 形式と重大な変更で、拡張機能を更新する必要があります。 詳細については、次を参照してください。[新機能については、Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)します。  
  
## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio ユーザー エクスペリエンス ガイドライン  
 拡張機能の UI を設計するための便利なヒントを取得[Visual Studio ユーザー エクスペリエンス ガイドライン](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)します。  
  
 高 DPI デバイスに美しく表示拡張機能を作成する方法を確認できます、[アドレス DPI 問題](../extensibility/addressing-dpi-issues2.md)記事。  
  
 利用、[イメージ サービスとカタログ](../extensibility/image-service-and-catalog.md)イメージの管理や高 DPI とテーマのサポート。  
  
## <a name="find-and-install-existing-visual-studio-extensions"></a>検索して、既存の Visual Studio 拡張機能のインストール  
 Visual Studio 拡張機能を見つけることができます、**拡張機能と更新**ダイアログで、**ツール**メニュー。 詳細については、次を参照してください。[検索と使用の Visual Studio Extensions](../ide/finding-and-using-visual-studio-extensions.md)します。 拡張機能を検索することも、 [Visual Studio marketplace](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Visual Studio SDK リファレンス  
 Visual Studio SDK の API リファレンスに見つかります[Visual Studio SDK リファレンス](../extensibility/visual-studio-sdk-reference.md)します。  
  
## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK のサンプル  
 Github の VS SDK 拡張機能のオープン ソースの例が見つかります[Visual Studio のサンプル](https://aka.ms/vs2015sdksamples)します。 この GitHub リポジトリには、Visual Studio のさまざまな拡張機能を示すサンプルが含まれています。  
  
## <a name="other-visual-studio-sdk-resources"></a>その他の Visual Studio SDK のリソース  
 使用することができます、VSSDK について質問があるか、拡張機能の開発経験を共有する場合、 [Visual Studio 機能拡張フォーラム](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)または[ExtendVS Gitter チャット ルーム](https://gitter.im/Microsoft/extendvs)します。  
  
 詳細を確認することができます、 [VSX Arcana ブログ](https://blogs.msdn.microsoft.com/vsx/)とブログの Microsoft Mvp によって書き込まれた数。  
  
-   [お気に入りの Visual Studio 拡張機能](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Visual Studio 機能拡張](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Visual Studio の拡張](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>関連項目  
 [メニュー コマンドを使用して拡張機能を作成します。](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [方法: 機能拡張プロジェクトを Visual Studio 2017 に移行](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)   
 [FAQ: アドインを VSPackage 拡張機能に変換します。](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [マネージ コード内の複数のスレッドを管理します。](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [メニューとコマンドを拡張します。](../extensibility/extending-menus-and-commands.md)   
 [ツールバーにコマンドを追加します。](../extensibility/adding-commands-to-toolbars.md)   
 [拡張し、カスタマイズ ツール ウィンドウ](../extensibility/extending-and-customizing-tool-windows.md)   
 [エディターと言語サービス拡張機能](../extensibility/editor-and-language-service-extensions.md)   
 [プロジェクトを拡張します。](../extensibility/extending-projects.md)   
 [ユーザー設定とオプションを拡張します。](../extensibility/extending-user-settings-and-options.md)   
 [カスタム プロジェクトと項目テンプレートを作成します。](../extensibility/creating-custom-project-and-item-templates.md)   
 [プロパティと、[プロパティ] ウィンドウを拡張します。](../extensibility/extending-properties-and-the-property-window.md)   
 [Visual Studio の他の部分を拡張します。](../extensibility/extending-other-parts-of-visual-studio.md)   
 [使用してサービスを提供します。](../extensibility/using-and-providing-services.md)   
 [Vspackage を管理します。](../extensibility/managing-vspackages.md)   
 [Visual Studio の分離シェル](../extensibility/visual-studio-isolated-shell.md)   
 [Visual Studio 拡張機能を出荷します。](../extensibility/shipping-visual-studio-extensions.md)   
 [Visual Studio SDK の内部](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Visual Studio SDK のサポート](../extensibility/support-for-the-visual-studio-sdk.md)   
 [アーカイブ](../extensibility/archive.md)   
 [Visual Studio SDK リファレンス](../extensibility/visual-studio-sdk-reference.md)
