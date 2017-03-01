---
title: "Visual Studio 2015 SDK の新機能 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 13
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
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: 8d77fce54b12b90f6a2632fd1c1741990be42a08
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Visual Studio 2015 SDK の新機能します。
Visual Studio SDK では、Visual Studio 2015、Visual Studio 2015 が更新されると、および Visual Studio 2017 の次の新規および更新の機能があります。  
  
## <a name="vs-2015-sdk-update-1"></a>VS 2015 SDK の更新プログラム 1  
 更新プログラム 1 では、配色テーマと Visual Studio イメージのサービスでうまく動作拡張機能のためのツールが含まれています。  
  
 これらのトピックでは、下にある、 [VSSDK ユーティリティ](../extensibility/internals/vssdk-utilities.md)セクション。  
  
-   [カラー テーマ ツール](../extensibility/internals/color-theming-tools.md)を作成し、Visual Studio のカスタム カラーを編集できます。  
  
-   [イメージ サービス ツール](../extensibility/internals/image-service-tools.md)Visual Studio イメージのマニフェスト ファイルを操作できます。  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Visual Studio SDK を Visual Studio に追加する新しい方法  
 Visual Studio 2015 以降がなくても、Visual Studio SDK を個別にダウンロードします。 代わりに、通常のインストール プロセスの一部としてインストールすることができますか、後でインストールすることもできます。 開くか、VSIX ソリューションを作成するときに Visual Studio に表示される Visual Studio Extensibility Tools をインストールします。 詳細については、次を参照してください。 [Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="new-ways-of-creating-extensions"></a>新しい拡張機能を作成する方法  
 以降、Visual Studio 2015 SDK では、使用しているプログラミング言語に応じて、拡張機能を作成するためのさまざまなオプションがあります。  
  
### <a name="visual-c-and-visual-basic"></a>Visual C# および Visual Basic  
 C# と Visual Basic の場合は、一連の vspackages にある、メニュー コマンド、ツール ウィンドウ、エディターの分類子、エディターの表示要素、およびエディターの余白の拡張機能を作成するためのプロジェクト項目テンプレートがあります。 標準の VSIX プロジェクトにこれらの一部またはすべてを追加することができます。 詳細については次を参照してください:  
  
-   [メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [ツール ウィンドウで、拡張機能を作成します。](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [エディター項目テンプレートを使用して拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [VSPackage で拡張機能を作成します。](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     不要になった、VSPackage ウィザードは、c# または Visual Basic で拡張機能を作成します。  
  
### <a name="c"></a>C++  
 C++ の場合は、VSPackage ウィザードは、メニュー コマンド、ツール ウィンドウ、およびカスタム エディターをサポートします。 検索で、**新しいプロジェクト** ダイアログ ボックス**Visual C/機能拡張**します。  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>NuGet 経由で VS SDK 参照アセンブリ  
 移植性の向上と機能拡張プロジェクトの共有は、VS SDK 参照アセンブリの NuGet バージョンを使用できます。  これらは、利用可能な[nuget.org](http://www.nuget.org)によって発行された[VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) 、プロジェクトまたは Visual Studio によるソリューションを簡単に追加できます**参照]、[管理 NuGet パッケージの**ダイアログ。 固有の機能拡張のアセンブリへの個別の参照を追加したり、すべての VS SDK は一度に VS SDK を使用してアセンブリを参照を追加したり[メタ パッケージ](http://www.nuget.org/packages/VSSDK_Reference_Assemblies)します。 NuGet の詳細については、次を参照してください。 [NuGet 概要](http://docs.nuget.org/)と[NuGet パッケージを使用して管理ダイアログ](http://docs.nuget.org/Consume/Package-Manager-Dialog)します。  
  
 VS SDK 参照アセンブリの NuGet バージョンを使用すると、別のユーザーを開き、プロジェクトをビルドする VS SDK をインストールする必要ありません。  NuGet の参照アセンブリと VS SDK ビルド ツールは、そのプロジェクトの自分のコンピューターに自動的にインストールされます。  
  
 VS SDK 項目テンプレートでは、NuGet の参照を使用し、既定で NuGet のメリットを享受するためのツールをビルドします。  
  
> [!NOTE]
>  まま、プロジェクトの VS SDK がインストールされている参照アセンブリを使用することができます (下にある\<Visual Studio のインストール場所 > \ VSSDK\VisualStudioIntegration\Common\Assemblies)、既存の機能拡張プロジェクトは、NuGet パッケージを使用してアップグレードする必要はありません。  プロジェクト**参照]、[参照の追加**ダイアログが VS SDK がインストールされている参照アセンブリを使用し続けます。  
>   
>  NuGet を使用する既存のプロジェクトを変更したい場合[方法: VSPackages を Visual Studio 2015 に移行](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)NuGet パッケージへの機能拡張プロジェクトを更新する方法のセクションが含まれています。  
  
## <a name="light-bulbs"></a>電球  
 拡張機能コードの記述の最も魅力的な新しい方法の&1; つは、Roslyn プロジェクトによって提供されます。 詳細については、次を参照してください。 [Roslyn](https://github.com/dotnet/Roslyn)します。  
  
 電球マークは、VSSDK に付属している新しい機能です。 これらは、展開して、一連のコードのリファクタリング操作または組み込みのコード アナライザーによって識別される問題の修正プログラムを表示する Visual Studio エディターで使用されるアイコンです。 詳細については、次を参照してください。[チュートリアル: 表示する Light Bulb 提案](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)します。  
  
## <a name="updated-user-experience-guidelines"></a>更新されたユーザー エクスペリエンス ガイドライン  
 Visual Studio の新しい拡張機能または機能を設計するでしょうか。 更新および拡張をチェック アウト[Visual Studio のユーザー エクスペリエンス ガイドライン](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)します。  見つかります、[トークンをカラー](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md)、[フォント サイズ](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)、[ダイアログのレイアウトの仕様](../extensibility/ux-guidelines/layout-for-visual-studio.md)、およびその他のガイダンスの Visual Studio で、新しい UI をシームレスに統合する必要があります。
