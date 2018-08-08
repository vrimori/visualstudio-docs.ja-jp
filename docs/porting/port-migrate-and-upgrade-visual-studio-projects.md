---
title: プロジェクトの移植、移行、およびアップグレード
description: 以前のバージョンの Visual Studio で作成されたプロジェクトに対する Visual Studio 2017 でのサポートと、Visual Studio がプロジェクトを移行する必要があるタイミングを決定する方法のリファレンス。
ms.date: 06/19/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload: multiple
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.openlocfilehash: 4bad722034657e3b58faaf665bfb0bc6ffcbe960
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513547"
---
# <a name="project-migration-and-upgrade-reference-for-visual-studio-2017"></a>Visual Studio 2017 のプロジェクトの移行とアップグレードのリファレンス

通常、新しいバージョンの Visual Studio はいずれも、以前の種類のプロジェクト、ファイル、その他のアセットに対応しています。 それらのオブジェクトは[これまでと同様に](../ide/solutions-and-projects-in-visual-studio.md)操作できます。新しい機能を利用していない場合でも、Visual Studio 2015、Visual Studio 2013、Visual Studio 2012 など、以前のバージョンとの下位互換性の維持が一般に試みられています。 (どの機能がどのバージョンに固有の機能であるかについては、[リリース ノート](https://visualstudio.microsoft.com/vs/release-notes/)を参照してください。)

一部の種類のプロジェクトに対するサポートは、今後変更される場合もあります。 新しいバージョンの Visual Studio では、特定のプロジェクトが一切サポートされなくなったり、下位互換性がないプロジェクトの更新が必要になったりすることがあります。 移行に関する問題の現在の状況については、[Visual Studio Developer Community のサイト](https://developercommunity.visualstudio.com)を参照してください。

現在、この記事では、Visual Studio 2017 の移行が可能なプロジェクト タイプに対してのみ詳細を提供しています。 この記事では、Visual Studio 2017 でサポートされなくなったことで移行できないプロジェクト タイプは除外されています。 また、移行に関する問題がないサポート対象のプロジェクト タイプ ([対象プラットフォームと互換性](/visualstudio/productinfo/vs2017-compatibility-vs)に関するページでその一覧を確認できます) もこの記事では除外されています。

> [!Important]
> 特定の種類のプロジェクトでは、Visual Studio インストーラーで適切なワークロードをインストールする必要があります。 ワークロードがインストールされていない場合、Visual Studio は不明な、または互換性のないプロジェクトの種類を報告します。 その場合、インストール オプションを確認して、やり直してください。 Visual Studio 2017 でサポートされているプロジェクトの詳細について、[対象プラットフォームと互換性](/visualstudio/productinfo/vs2017-compatibility-vs)に関する記事をもう一度ご覧ください。

## <a name="project-types"></a>プロジェクトの種類

次の一覧は、Visual Studio 2017 より前のバージョンで作成されたプロジェクトに対する Visual Studio 2017 でのサポートをまとめたものです。

一覧表示されるべきプロジェクトやファイルの種類が見つからない場合は、[この記事の Visual Studio 2015 バージョン](port-migrate-and-upgrade-visual-studio-projects.md)をご覧になり、このページの下の "ドキュメントのフィードバックを送る" オプションを使用して、プロジェクトの詳細をお知らせください。 (応答する場合は、匿名の [このページは役に立ちましたか] コントロールではなく、ドキュメントに関するフィードバックを使ってください )

| プロジェクトの種類 | サポート |
| --- | --- |
| .NET Core プロジェクト (xproj) | Visual Studio 2015 で作成したプロジェクトでは、.xproj プロジェクト ファイルが含まれるプレビュー ツールが使用されていました。 Visual Studio 2017 で .xproj ファイルを開くと、ファイルを .csproj 形式に移行するように求められます (.xproj ファイルのバックアップが作成されます)。 .NET Core プロジェクトのこの .csproj 形式は、Visual Studio 2015 以前のバージョンではサポートされていません。  xproj 形式は csproj に移行しなければ Visual Studio 2017 で利用できません。 詳細については、「[.NET Core プロジェクトから .csproj 形式への移行](/dotnet/core/migration/#visual-studio-2017)」をご覧ください。|
| ASP.NET Web アプリケーションと ASP.NET Core Web アプリケーション (Application Insights が有効) | Visual Studio のユーザーごとのリソース情報がユーザー インスタンス別にレジストリに保存されます。 この情報は、プロジェクトを開いていない状態で Azure Application Insights データを検索するときに利用されます。 Visual Studio 2015 では、Visual Studio 2017 とは異なるレジストリの場所が使用され、競合しません。<br/><br/>ユーザーが ASP.NET Web アプリケーションまたは ASP.NET Core Web アプリケーションを作成すると、リソースは .suo ファイルに保存されます。 ユーザーは Visual Studio 2015 や 2017 でプロジェクトを開くことができます。両方のバージョンで使用されているプロジェクトとソリューションが Visual Studio でサポートされている限り、両方でリソース情報が使用されます。 ユーザーは製品ごとに 1 回認証する必要があります。 たとえば、Visual Studio 2015 で作成されたプロジェクトを Visual Studio 2017 で開く場合、Visual Studio 2017 で認証が要求されます。 |
| C#/Visual Basic Webform または Windows フォーム | プロジェクトを Visual Studio 2017 と Visual Studio 2015 で開くことができます。 |
| データベース単体テスト プロジェクト (csproj、.vbproj) | 古いデータ単体テスト プロジェクトは Visual Studio 2017 で読み込まれますが、依存関係は GAC に保存されているものが使用されます。 単体テスト プロジェクトをアップグレードし、最新の依存関係を使用するには、ソリューション エクスプローラーでプロジェクトを右クリックし、**[SQL Server 単体テスト プロジェクトに変換する]** を選択します。 |
| F# | Visual Studio 2017 では、Visual Studio 2013 と 2015 で作成したプロジェクトを開くことができます。 ただし、これらのプロジェクトで Visual Studio 2017 機能を有効にするには、プロジェクトのプロパティを開き、ターゲットの fsharp.core を F# 4.1 に変更します。 .NET ワークロードの場合、Visual Studio インストーラーの **[F# 言語サポート]** オプションは既定では選択されないことにもご注意ください。ワークロードにこのオプションを選択するか、**[開発作業]** の **[個別のコンポーネント]** から選択する方法で追加する必要があります。 |
| InstallShield<br/>MSI のセットアップ | Visual Studio 2010 で作成されたインストーラー プロジェクトは、[Visual Studio Installer Projects の拡張機能](https://marketplace.visualstudio.com/items?itemName=UnniRavindranathan-MSFT.MicrosoftVisualStudio2013InstallerProjects)を使って以降のバージョンで開くことができます。 「[WiX Toolset Visual Studio 2017 Extension](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)」も参照してください。 InstallShield Limited Edition は、Visual Studio に付属しなくなりました。 Visual Studio 2017 で利用可能かどうかについては、[Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) にご確認ください。 |
| LightSwitch | LightSwitch は Visual Studio 2017 ではサポートされていません。 Visual Studio 2012 以前のバージョンで作成されたプロジェクトを Visual Studio 2013 または Visual Studio 2015 で開くとアップグレードされ、以後、Visual Studio 2013 または Visual Studio 2015 のみで開けるようになります。 |
| Microsoft Azure Tools for Visual Studio | これらの種類のプロジェクトを開くには、最初に [Azure SDK for .NET](http://azure.microsoft.com/downloads/)をインストールした後、プロジェクトを開きます。 必要に応じて、プロジェクトが更新されます。 |
| モデル ビュー コントローラー フレームワーク (ASP.NET MVC) | MVC バージョンと Visual Studio のサポート:<ul><li>Visual Studio 2010 SP1 は MVC 2 と MVC 3 をサポートしています。MVC 4 サポートは [ASP.NET 4 MVC 4 for Visual Studio 2010 SP1 をダウンロード](https://www.microsoft.com/download/details.aspx?id=30683)すると追加されます。</li><li>Visual Studio 2012 は MVC 3 と MVC 4 のみをサポートしています。</li><li>Visual Studio 2013 は MVC 4 と MVC 5 のみをサポートしています。</li><li>Visual Studio 2017 と Visual Studio 2015 は MVC 4 (既存のオブジェクトを開くことはできますが、新規作成はできません) と MVC 5 をサポートしています。</li></ul><br/>MVC バージョンをアップグレードする:<ul><li>MVC 2 から MVC 3 に自動的にアップグレードする方法については、「[ASP.NET MVC 3 Application Upgrader](http://go.microsoft.com/fwlink/?LinkID=238178)」 (ASP.NET MVC 3 アプリケーション アップグレード プログラム) を参照してください。</li><li>MVC 2 から MVC 3 に手動でアップグレードする方法については、「 [Upgrading an ASP.NET MVC 2 Project to ASP.NET MVC 3 Tools Update (ASP.NET MVC 2 プロジェクトから ASP.NET MVC 3 Tools Update へのアップグレード)](http://go.microsoft.com/fwlink/?linkid=238178)」を参照してください。</li><li>MVC 3 から MVC 4 に手動でアップグレードする方法については、「 [Upgrading an ASP.NET MVC 3 Project to ASP.NET MVC 4 (ASP.NET MVC 3 プロジェクトから ASP.NET MVC 4 へのアップグレード)](http://www.asp.net/whitepapers/mvc4-release-notes)」を参照してください。 .NET Framework 3.5 SP1 を対象とするプロジェクトの場合は、.NET Framework 4 を使用するようにプロジェクトの対象を変更する必要があります。</li><li>MVC 4 から MVC 5 に手動でアップグレードする方法については、「[How to Upgrade an ASP.NET MVC 4 and Web API Project to ASP.NET MVC 5 and Web API 2](https://www.asp.net/mvc/overview/releases/how-to-upgrade-an-aspnet-mvc-4-and-web-api-project-to-aspnet-mvc-5-and-web-api-2) (ASP.NET MVC 4 と Web API プロジェクトを ASP.NET MVC 5 と Web API 2 にアップグレードする方法)」を参照してください。</li></ul> |
| モデリング | Visual Studio でプロジェクトを自動的に更新することを許可した場合は、Visual Studio 2015、Visual Studio 2013、または Visual Studio 2012 で開くことができます。<br/><br/>モデリング プロジェクトの形式は Visual Studio 2015 と Visual Studio 2017 の間で変わっていません。プロジェクトはいずれのバージョンでも開き、変更できます。 ただし、Visual Studio 2017 では動作に違いがあります。<ul><li>メニューとテンプレートで、モデリング プロジェクトの名称が "依存関係の検証" になりました。</li><li>UML 図は Visual Studio 2017 ではサポートされていません。 UML ファイルは以前と同様にソリューション エクスプローラーに一覧表示されますが、XML ファイルが開きます。 UML 図を表示、作成、編集するには、Visual Studio 2015 を使用してください。</li><li>Visual Studio 2017 では、モデリング プロジェクトが構築されるとき、アーキテクチャの依存関係検証がなくなりました。 代わりに、コード プロジェクトが構築されるときに検証が実行されます。 この変更がモデリング プロジェクトに影響を与えることはありませんが、検証されるコード プロジェクトを変更する必要があります。 Visual Studio 2017 では、コード プロジェクトを必要に応じて自動的に変更できます ([詳細](http://go.microsoft.com/fwlink/?LinkId=827800))。</li></ul> |
| MSI セットアップ (vdproj) | InstallShield プロジェクトをご覧ください。 |
| Office 2007 VSTO | Visual Studio 2017 への一方向のアップグレードが必要です。 |
| Office 2010 VSTO | .NET Framework 4 を対象とするプロジェクトの場合は、Visual Studio 2010 SP1 以降でこのプロジェクトを開くことができます。 他のすべてのプロジェクトは、一方向のアップグレードが必要です。 |
| Service Fabric (sfproj) | Service Fabric アプリケーション プロジェクトが ASP.NET Core サービス プロジェクトを参照していない限り、Service Fabric アプリケーション プロジェクトは Visual Studio 2015 または Visual Studio 2017 のいずれかで開くことができます。 Visual Studio 2017 で開かれている Visual Studio 2015 からの Service Fabric プロジェクトは、xproj 形式から csproj への一方向の移行が行われます。 この表で前述した「.NET Core プロジェクト (xproj)」を参照してください。 |
| SharePoint 2010 | SharePoint ソリューション プロジェクトを Visual Studio 2017 で開くと、SharePoint 2013 または SharePoint 2016 にアップグレードされます。 アップグレードのためには、".NET デスクトップ開発" ワークロードを Visual Studio 2017 にインストールする必要があります。<br/><br/>SharePoint プロジェクトのアップグレード方法について詳しくは、「[SharePoint 2013 へのアップグレード](https://technet.microsoft.com/library/cc303420.aspx)」、「[SharePoint Server 2013 でワークフローを更新する](https://technet.microsoft.com/library/dn133867.aspx)」、および「[データベース接続アップグレード用の SharePoint Server 2016 ファームを作成する](https://technet.microsoft.com/library/cc263026(v=office.16).aspx)」をご覧ください。 |
| SharePoint 2016 | Office Developer Tools Preview 2 で作成された SharePoint アドイン プロジェクトを Visual Studio 2017 で開くことはできません。 この制限を回避するには、csproj vbproj ファイルで、`MinimumVisualStudioVersion` を 12.0 に、`MinimumOfficeToolsVersion` を 12.2 に更新する必要があります。 |
| Silverlight | Silverlight プロジェクトは Visual Studio 2017 ではサポートされていません。 Silverlight アプリケーションを維持するには、引き続き Visual Studio 2015 を使用してください。 |
| SQL Server Reporting Services および SQL Server Analysis Services (SSRS、SSDT、SSAS、MSAS) | これらのプロジェクトの種類は、Visual Studio ギャラリーの 2 つの拡張機能である [Microsoft Analysis Services Modeling Projects](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects) と [Microsoft Reporting Services Projects](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio) でサポートされています。 Visual Studio 2017 のデータの保存と処理のワークロードには SSDT のサポートも含まれます。 |
| SQL Server Integration Services (SSIS) | Visual Studio 2017 のサポートは、SQL Server Data Tools (SSDT) から使用できます。 詳細については、[SQL Server Integration Services のブログ](https://blogs.msdn.microsoft.com/ssis/2017/08/23/ssis-designer-is-now-available-for-visual-studio-2017/)をご覧ください。 |
| Visual C++ | Visual Studio 2017 を使用して、Visual Studio 2010 以降の Visual Studio で作成されたプロジェクトを操作できます。 プロジェクトを初めて開いたときに、最新のコンパイラとツールセットにアップグレードするか、元のプロジェクトを引き続き使用するかを選択できます。 元のプロジェクトを引き続き使用することを選択した場合、Visual Studio 2017 はプロジェクト ファイルを変更せず、以前の Visual Studio のインストールのツールセットを使用してプロジェクトをビルドします。 元のオプションを維持すると、必要に応じて、Visual Studio の元のバージョンでプロジェクトを開くことができます。 詳細については、「[Visual Studio でネイティブ マルチ ターゲットを利用し、古いプロジェクトを作成する](/cpp/porting/use-native-multi-targeting)」を参照してください。 |
| Visual Studio 拡張性/VSIX | MinimumVersion 14.0 以前のプロジェクトは、MinimumVersion 15.0 を宣言するように更新されます。この宣言により、前のバージョンの Visual Studio でプロジェクトを開けなくなります。 前のバージョンでプロジェクトを開くには、MinimumVersion を `$(VisualStudioVersion)` に設定します。 「[How to: Migrate Extensibility Projects to Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)」 (方法: 機能拡張プロジェクトの Visual Studio 2017 への移行) も参照してください。 |
| Visual Studio Lab Management | Microsoft Test Manager または Visual Studio 2010 SP1 以降を利用し、これらのバージョンで差制された環境を開くことができます。 ただし、Visual Studio 2010 SP1 の場合、環境を作成するには、使用している Microsoft Test Manager のバージョンが Team Foundation Server のバージョンと一致する必要があります。 |
| Visual Studio Tools for Apache Cordova | プロジェクトは Visual Studio 2017 で開くことができますが、下位互換性はありません。 Visual Studio 2015 からプロジェクトを開くと、プロジェクトを変更するように求められます。 この変更により、`taco.json` ファイルの代わりにツールセットを利用し、Cordova ライブラリのバージョン、そのプラットフォームとプラグイン、そのノード/npm 依存関係を管理するようにプロジェクトがアップグレードされます。 詳細については、[移行ガイド](https://docs.microsoft.com/visualstudio/cross-platform/tools-for-cordova/first-steps/migrate-from-visual-studio-2015)を参照してください。 |
| Web 配置 (wdproj) | 発行プロファイルのサポートが追加されたことで、Visual Studio 2012 では Web 配置プロジェクトのサポートが削除されました。 Visual Studio 2017 には等価なものがないため、そのようなプロジェクトの自動移行パスはありません。 そこで、[StackOverflow](https://stackoverflow.com/a/12061065/1203388) に説明されているように、テキスト エディターで wdproj ファイルを開き、pubxml (発行プロファイル) ファイルに任意のカスタマイズをコピーおよび貼り付けます。 「[Plans regarding website and web deployment projects (MSDN blogs)](https://blogs.msdn.microsoft.com/webdev/2012/08/06/plans-regarding-website-projects-and-web-deployment-projects)」 (Web サイトおよび Web 配置プロジェクトに関する計画 (MSDN ブログ)) も参照してください。 |
| Windows Communication Foundation、Windows Workflow Foundation | このプロジェクトは、Visual Studio 2017、Visual Studio 2015、Visual Studio 2013、Visual Studio 2012 で開くことができます。 |
| Windows Presentation Foundation | このプロジェクトは、Visual Studio 2013、Visual Studio 2012、Visual Studio 2010 SP1 で開くことができます。 |
| Windows ストア/フォン アプリ | Visual Studio 2017 では、Windows Store 8.1 と 8.0 または Windows Phone 8.1 と 8.0 のプロジェクトはサポートされていません。 これらのアプリを維持するには、引き続き Visual Studio 2015 を使用してください。 Windows Phone 7.x プロジェクトを維持するには、Visual Studio 2012 を使用してください。 |

## <a name="how-visual-studio-decides-when-to-migrate-a-project"></a>Visual Studio がプロジェクトを移行するタイミングを決定する方法

Visual Studio の各新規バージョンでは、一般に、バージョンが異なっても同じプロジェクトを開き、変更し、ビルドできるように、以前のバージョンとの互換性が維持されます。 ただし、時間の経過と共に、一部のプロジェクトの種類のサポート終了など、避けられない変更が発生します (Visual Studio 2017 でサポートされているプロジェクトの種類については「[Visual Studio 2017 の対象プラットフォームと互換性](/visualstudio/productinfo/vs2017-compatibility-vs)」をご覧ください)。このような場合、新しいバージョンの Visual Studio はプロジェクトを読み込まず、移行パスを提供しません。そのようなプロジェクトは、それをサポートしている以前のバージョンの Visual Studio で管理する必要があります。

つまり、新しいバージョンの Visual Studio ではプロジェクトを開くことはできますが、以前のバージョンとの互換性がなくなる可能性がある方法でプロジェクトを更新または移行する必要があります。 Visual Studio は、複数の条件を使って、このような移行が必要かどうかを判断します。

- Visual Studio 2013 RTM まで遡る、プラットフォームのターゲット バージョンとの互換性。

- 以前のバージョンの Visual Studio との、デザイン時資産の互換性 (つまり、Visual Studio 2017 の異なるチャネル、Visual Studio 2015 RTM & Update 3、Visual Studio 2013 RTM & Update 5、Visual Studio 2012 Update 4、Visual Studio 2010 SP 1)。Visual Studio 2017 は、以前のバージョンでプロジェクトをまだ開くことができるように、非推奨のデザイン時資産を、破壊することなく正常に失敗させます。

- 新しいデザイン時資産により、Visual Studio 2013 RTM & Update 5 までの以前のバージョンとの互換性がなくなるかどうか。

対象のプロジェクトの種類のエンジニアリング所有者は、これらの条件を調べて、サポート、互換性、移行に関して問題があるときは問い合わせます。 ここでも、Visual Studio は、可能であれば Visual Studio のバージョン間の透過的な互換性を維持します。つまり、Visual Studio のあるバージョンで作成および変更したプロジェクトは、他のバージョンでもそのままで動作します。

ただし、この記事で説明されている一部のプロジェクトの種類のように、このような互換性が不可能な場合は、Visual Studio はアップグレード ウィザードを開いて必要な一方向の変更を行います。

このような一方向の変更には、プロジェクト ファイルでの `ToolsVersion` プロパティの変更が含まれます。これは、最終的に必要な実行可能で配置可能なアーティファクトにプロジェクトのソース コードを変換できる MSBuild の正確なバージョンを示します。 つまり、プロジェクトと以前のバージョンの Visual Studio との互換性を損なうものは、*Visual Studio* のバージョンではなく、`ToolsVersion` によって決定される *MSBuild* のバージョンです。 お使いの Visual Studio のバージョンに、プロジェクトでの `ToolsVersion` と一致する MSBuild ツールチェーンが含まれている限り、Visual Studio をそのツールチェーンを呼び出してプロジェクトをビルドできます。

以前のバージョンで作成されたプロジェクトとの最大限の互換性を維持するため、Visual Studio 2017 には、`ToolsVersion` 15、14、12、4 をサポートするために必要な MSBuild ツールチェーンが含まれています。 これらの `ToolsVersion` 値のいずれかを使うプロジェクトでは、ビルドが成功するはずです (やはり、「[Visual Studio 2017 の対象プラットフォームと互換性](/visualstudio/productinfo/vs2017-compatibility-vs)」で説明されているように、Visual Studio 2017 がプロジェクトの種類をサポートするかどうかに依存します)。

このコンテキストでの必然的な疑問は、新しい `ToolsVersion` 値にプロジェクトを手動で更新または移行する必要があるかどうかということです。 そのような変更は不要であり、行うと、修正するにはプロジェクトの再ビルドが必要な多くのエラーと警告が発生する可能性があります。 さらに、将来 Visual Studio が特定の `ToolsVersion` をサポートしなくなった場合、プロジェクトを開くと、`ToolsVersion` の値を変更する必要があるため、プロジェクト移行プロセスが開始されます。 そのような場合、その特定のプロジェクトの種類のサブシステムは、変更が必要なものを正確に知っており、この記事で前述したように自動的にこれらの変更を行うことができます。

詳しくは、次の記事をご覧ください。

- [ToolsVersion ガイダンス](../msbuild/msbuild-toolset-toolsversion.md)
- [フレームワーク対象設定機能ガイダンス](../ide/visual-studio-multi-targeting-overview.md)
