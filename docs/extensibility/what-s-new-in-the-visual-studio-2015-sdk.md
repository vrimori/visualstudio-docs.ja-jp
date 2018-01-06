---
title: "どのような &#39; Visual Studio 2015 SDK の |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1008e1c81c6d99bc9fa0615263cf023a56101435
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2018
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>どのような &#39; Visual Studio 2015 SDK の
Visual Studio SDK では、Visual Studio 2015、Visual Studio 2015 更新、および Visual Studio 2017 の新規および更新の機能が次があります。  
  
## <a name="vs-2015-sdk-update-1"></a>VS 2015 SDK の更新プログラム 1  
 更新プログラム 1 では、配色テーマと Visual Studio イメージ サービスと共に動作拡張機能のためのツールが含まれます。  
  
 これらのトピックでは、下にある、 [VSSDK ユーティリティ](../extensibility/internals/vssdk-utilities.md)セクション。  
  
-   [カラー テーマ ツール](../extensibility/internals/color-theming-tools.md)を作成し、Visual Studio のカスタム カラーを編集できます。  
  
-   [イメージ サービス ツール](../extensibility/internals/image-service-tools.md)Visual Studio イメージ マニフェスト ファイルで作業することができます。  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Visual Studio に Visual Studio SDK を追加する新しい方法  
 Visual Studio 2015 以降、する必要はありません、Visual Studio SDK を個別にダウンロードします。 代わりに、通常のインストール プロセスの一環としてインストールすることができますか、後でインストールすることもできます。 開く、VSIX ソリューションを作成したりすると、Visual Studio が Visual Studio 機能拡張ツールをインストールするように求められます。 詳細については、次を参照してください。 [、Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="new-ways-of-creating-extensions"></a>拡張機能を作成する新しい方法  
 使用しているプログラミング言語に応じて、拡張機能を作成するためのさまざまなオプションがある以降、Visual Studio 2015 SDK では、します。  
  
### <a name="visual-c-and-visual-basic"></a>Visual C# および Visual Basic  
 C# と Visual Basic の場合は、Vspackage、メニュー コマンド、ツール ウィンドウ、エディター分類子、エディターの表示要素、およびエディターの余白の拡張機能を作成するためのプロジェクト項目テンプレートの全範囲があります。 標準の VSIX プロジェクトにこれらの一部またはすべてを追加することができます。 詳細については次を参照してください:  
  
-   [メニュー コマンドを使用した拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [ツール ウィンドウでの拡張機能の作成](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [エディターの項目テンプレートを使用した拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [VSPackage を使用した拡張機能の作成](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     VSPackage ウィザードは、c# または Visual Basic で不要になった拡張機能を作成します。  
  
### <a name="c"></a>C++  
 C++ の場合は、VSPackage ウィザードは、メニュー コマンド、ツール ウィンドウ、およびカスタム エディターをサポートします。 検索で、**新しいプロジェクト**でダイアログ**Visual C/機能拡張**です。  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>NuGet 経由で VS SDK の参照アセンブリ  
 移植性の向上と機能拡張プロジェクトの共有は、NuGet のバージョンの VS SDK の参照アセンブリを使用できます。  これらで使用できる[nuget.org](http://www.nuget.org)によって発行された[VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility)プロジェクトまたは Visual Studio によるソリューションを簡単に追加して**参照/管理 NuGetパッケージ**ダイアログ。 特定の拡張機能アセンブリへの個々 の参照を追加したり、VS SDK のすべてが一度に VS SDK を使用してアセンブリを参照を追加したり[メタ パッケージ](http://www.nuget.org/packages/VSSDK_Reference_Assemblies)です。 NuGet の詳細については、次を参照してください。、 [NuGet のドキュメント](/NuGet)と[パッケージ マネージャー UI](/NuGet/Tools/Package-Manager-UI)トピックです。  
  
 NuGet のバージョンの VS SDK の参照アセンブリを使用して、別のユーザーが開くし、プロジェクトをビルドする VS SDK をインストールする必要はありません。  NuGet の参照アセンブリ、VS SDK ビルド ツールは、そのプロジェクトの自分のコンピューターに自動的にインストールされます。  
  
 VS SDK 項目テンプレートでは、NuGet を使用して、それらの参照用と、既定では、NuGet の利点を取得するためのビルド ツールを使用します。  
  
> [!NOTE]
>  アセンブリを使用して、VS SDK がインストールされている参照プロジェクトで続行することができます (下にある\<Visual Studio のインストール場所 > \ VSSDK\VisualStudioIntegration\Common\Assemblies)、既存の機能拡張プロジェクトがある必要はありませんNuGet パッケージを使用するアップグレードされます。  プロジェクト**参照/参照の追加**ダイアログがインストールされている VS SDK の参照アセンブリを使用し続けます。  
>   
>  NuGet を使用して、参照して、既存のプロジェクトを変更したい場合[する方法: Visual Studio 2015 への移行の Vspackage](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) NuGet パッケージへの機能拡張プロジェクトを更新する方法のセクションが含まれています。  
  
## <a name="light-bulbs"></a>電球  
 拡張機能コードの記述最も魅力的な新しい方法の 1 つは、Roslyn プロジェクトによって提供されます。 詳細については、次を参照してください。 [Roslyn](https://github.com/dotnet/Roslyn)です。  
  
 電球マークは付属して VSSDK する新機能です。 これらは、展開すると、一連のコードのリファクタリング操作または組み込みのコード アナライザーによって識別される問題の修正プログラムを表示する、Visual Studio エディターで使用されるアイコンです。 詳細については、次を参照してください。[チュートリアル: 電球の推奨事項を表示する](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)です。  
  
## <a name="updated-user-experience-guidelines"></a>更新されたユーザー エクスペリエンス ガイドライン  
 Visual Studio の新しい拡張機能または機能を設計しますか。 更新と展開をチェック アウト[Visual Studio ユーザー エクスペリエンス ガイドライン](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)です。  見つかります、[トークンの色](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md)、[フォント サイズ](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)、[ダイアログのレイアウトの仕様](../extensibility/ux-guidelines/layout-for-visual-studio.md)、およびその他のガイダンスの Visual Studio で新しい UI をシームレスに統合する必要があります。