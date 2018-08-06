---
title: どのような&#39;、Visual Studio 2015 SDK の新 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4926ed9fafb64664d3ac0426466d90611cae4450
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566694"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>どのような&#39;s を Visual Studio 2015 SDK の新機能
Visual Studio SDK では、Visual Studio 2015、Visual Studio 2015 が更新されると、および Visual Studio 2017 の新規および更新の機能が次があります。  
  
## <a name="vs-2015-sdk-update-1"></a>VS 2015 SDK の更新プログラム 1  
 更新プログラム 1 には、配色テーマと Visual Studio イメージ サービスと共に動作拡張機能のためのツールが含まれています。  
  
 これらのトピックでは、下、 [VSSDK ユーティリティ](../extensibility/internals/vssdk-utilities.md)セクション。  
  
-   [色のテーマのツール](../extensibility/internals/color-theming-tools.md)作成し、Visual Studio のカスタム色を編集できます。  
  
-   [イメージ サービス ツール](../extensibility/internals/image-service-tools.md)Visual Studio のイメージのマニフェスト ファイルを操作できます。  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Visual Studio SDK を Visual Studio に追加する新しい方法  
 Visual Studio 2015 以降、Visual Studio SDK を個別にダウンロードする必要はありません。 代わりに、通常のインストール プロセスの一部としてインストールすることができますか、後でインストールすることもできます。 開くか、VSIX ソリューションを作成するときに Visual Studio から Visual Studio 機能拡張ツールのインストールを求められます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="new-ways-of-creating-extensions"></a>新しい拡張機能を作成する方法  
 以降、Visual Studio 2015 SDK では、プログラミング言語に応じて使用している、拡張機能を作成するためのさまざまなオプションがあります。  
  
### <a name="visual-c-and-visual-basic"></a>Visual C# および Visual Basic  
 C# と Visual Basic の場合は、Vspackage、メニュー コマンド、ツール ウィンドウ、エディターの分類子、エディターの表示要素、およびエディターの余白の拡張機能を作成するためのプロジェクト項目テンプレートの完全な範囲があります。 標準の VSIX プロジェクトには、これらのテンプレートの一部またはすべてを追加できます。 詳細については次を参照してください:  
  
-   [メニュー コマンドを使用して拡張機能を作成します。](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [ツール ウィンドウでの拡張機能を作成します。](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [エディターの項目テンプレートを使用した拡張機能を作成します。](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [VSPackage を使用した拡張機能を作成します。](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     VSPackage のウィザードは、c# または Visual Basic で不要になった拡張機能を作成します。  
  
### <a name="c"></a>C++  
 C++ の場合は、VSPackage ウィザードは、メニュー コマンド、ツール ウィンドウ、およびカスタム エディターをサポートします。 探し、**新しいプロジェクト**でダイアログ**Visual C/機能拡張**します。  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>NuGet を使用して VS SDK 参照アセンブリ  
 移植性の向上と機能拡張プロジェクトの共有は、VS SDK の参照アセンブリの NuGet のバージョンを使用できます。 これらのアセンブリは[nuget.org](http://www.nuget.org)によって発行された[VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility)プロジェクトまたは Visual Studio でソリューションに簡単に追加できると**参照/管理NuGet パッケージの**ダイアログ。 固有の機能拡張アセンブリに個々 の参照を追加したり、すべての VS SDK を一度に VS SDK を使用してアセンブリの参照を追加[メタ パッケージ](http://www.nuget.org/packages/VSSDK_Reference_Assemblies)します。 NuGet の詳細については、次を参照してください。、 [NuGet のドキュメント](/NuGet)と[パッケージ マネージャー UI](/NuGet/Tools/Package-Manager-UI)トピック。  
  
 VS SDK の参照アセンブリの NuGet のバージョンを使用して、別のユーザーはいないを開いて、プロジェクトをビルドする VS SDK をインストールする必要があります。  NuGet 参照アセンブリと VS SDK ビルド ツールは、そのプロジェクトの自分のコンピューターに自動的にインストールされます。  
  
 VS SDK の項目テンプレートは、NuGet の参照を使用し、ビルド ツールが既定で NuGet の特典を利用します。  
  
> [!NOTE]
>  VS SDK がインストールされている参照アセンブリをプロジェクトで使用する続行することができます (下にある\<Visual Studio のインストール場所 > \ VSSDK\VisualStudioIntegration\Common\Assemblies)、既存の機能拡張プロジェクトがある必要はありませんアップグレードすると、NuGet パッケージを使用します。  プロジェクト**参照]、[参照の追加**VS SDK がインストールされている参照アセンブリを使用するダイアログが続行されます。  
>   
>  NuGet を使用して、参照してください、既存のプロジェクトを変更したい場合[方法: Visual Studio 2015 への移行の Vspackage](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) NuGet パッケージへの拡張機能プロジェクトを更新する方法のセクションがあります。  
  
## <a name="light-bulbs"></a>電球  
 拡張機能コードの記述の最も魅力的な新しい方法の 1 つは、Roslyn プロジェクトによって提供されます。 詳細については、次を参照してください。 [Roslyn](https://github.com/dotnet/Roslyn)します。  
  
 電球マークは VSSDK に付属する新しい機能です。 Visual Studio エディターで使用される、展開すると、一連のコードのリファクタリング操作または組み込みのコード アナライザーによって識別された問題の修正プログラムを表示するアイコンが表示されます。 詳細については、次を参照してください。[チュートリアル: を表示する Light Bulb Suggestions](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)します。  
  
## <a name="updated-user-experience-guidelines"></a>更新されたユーザー エクスペリエンス ガイドライン  
 Visual Studio の新しい拡張機能または機能を設計しますか。 更新と展開をチェック アウト[Visual Studio ユーザー エクスペリエンス ガイドライン](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)します。  見つかります、[色のトークン](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md)、[フォント サイズ](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)、[ダイアログのレイアウトの仕様](../extensibility/ux-guidelines/layout-for-visual-studio.md)、および Visual Studio と、新しい UI をシームレスに統合する必要があるその他のガイダンス。