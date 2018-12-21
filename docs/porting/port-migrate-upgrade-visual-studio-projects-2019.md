---
title: Visual Studio 2019 プレビューでのプロジェクトの移植、移行、およびアップグレード
titleSuffix: ''
description: 以前のバージョンの Visual Studio で作成されたプロジェクトに対する Visual Studio 2019 Preview でのサポートと、Visual Studio がプロジェクトを移行するタイミングを決定する方法のリファレンス。
ms.date: 12/06/2018
ms.prod: visual-studio-dev16
ms.technology: vs-ide-general
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
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
ms.openlocfilehash: c393d6f9fbd239ab38957f66161bcff7372ac45f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058664"
---
# <a name="project-migration-and-upgrade-reference-for-visual-studio-2019-preview"></a>Visual Studio 2019 Preview のプロジェクトの移行とアップグレードのリファレンス

通常、新しいバージョンの Visual Studio はいずれも、以前の種類のプロジェクト、ファイル、その他のアセットに対応しています。 それらのオブジェクトは[これまでと同様に](../ide/solutions-and-projects-in-visual-studio.md)操作できます。新しい機能を利用していない場合でも、Visual Studio 2017、Visual Studio 2015、Visual Studio 2013、Visual Studio 2012 など、以前のバージョンとの下位互換性の維持が一般に試みられています。 (どの機能がどのバージョンに固有の機能であるかについては、[リリース ノート](/visualstudio/releases/2019/release-notes-preview)を参照してください。)

一部の種類のプロジェクトに対するサポートは、今後変更される場合もあります。 新しいバージョンの Visual Studio では、特定のプロジェクトが一切サポートされなくなったり、下位互換性がなくったためにプロジェクトの更新が必要になったりすることがあります。 移行に関する問題の現在の状況については、[Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com)を参照してください。

この記事では、Visual Studio 2019 Preview の移行が可能なプロジェクト タイプに対する詳細を提供しています。 また、Visual Studio 2019 Preview で非推奨となった、または近いうちに非推奨となるプロジェクト タイプに関する詳細も提供します。 この記事では、Visual Studio 2019 でサポートされなくなったことで移行できないプロジェクト タイプは除外されています。 また、移行に関する問題がないサポート対象のプロジェクト タイプ ([対象プラットフォームと互換性](/visualstudio/releases/2019/compatibility)に関するページでその一覧を確認できます) もこの記事では除外されています。

> [!Important]
> 特定のプロジェクト タイプでは、Visual Studio インストーラーを通じて特定のワークロードをインストールする必要があります。 ワークロードがインストールされていない場合、Visual Studio は不明な、または互換性のないプロジェクトの種類を報告します。 その場合、インストール オプションを確認して、やり直してください。 Visual Studio 2019 Preview でサポートされているプロジェクトの詳細については、[対象プラットフォームと互換性](/visualstudio/releases/2019/compatibility)に関する記事をご覧ください。

## <a name="project-types"></a>プロジェクトの種類

次の一覧は、Visual Studio 2019 Preview より前のバージョンで作成されたプロジェクトに対する Visual Studio 2019 Preview でのサポートをまとめたものです。

一覧表示されるべきプロジェクトやファイルの種類が見つからない場合は、[この記事の Visual Studio 2017 バージョン](port-migrate-and-upgrade-visual-studio-projects.md)をご覧になり、このページの下の "ドキュメントのフィードバックを送る" オプションを使用して、プロジェクトの詳細をお知らせください。 (応答する場合は、匿名の [このページは役に立ちましたか] コントロールではなく、ドキュメントに関するフィードバックを使ってください )

| プロジェクトの種類 | サポート |
| --- | --- |
| .NET Core プロジェクト (xproj) | Visual Studio 2015 で作成したプロジェクトでは、.xproj プロジェクト ファイルが含まれるプレビュー ツールが使用されていました。 Visual Studio 2019 Preview で .xproj ファイルを開くと、ファイルを .csproj 形式に移行するように求められます (.xproj ファイルのバックアップが作成されます)。 .NET Core プロジェクトのこの .csproj 形式は、Visual Studio 2015 以前のバージョンではサポートされていません。  xproj 形式は csproj に移行しなければ Visual Studio 2017 以降で利用できません。 詳細については、「[.NET Core プロジェクトから .csproj 形式への移行](/dotnet/core/migration/#visual-studio-2017)」をご覧ください。|
| ASP.NET Web アプリケーションと ASP.NET Core Web アプリケーション (Application Insights が有効) | Visual Studio のユーザーごとのリソース情報がユーザー インスタンス別にレジストリに保存されます。 この情報は、プロジェクトを開いていない状態で Azure Application Insights データを検索するときに利用されます。 Visual Studio 2015 では、Visual Studio 2017 および Visual Studio 2019 Preview とは異なるレジストリの場所が使用され、競合しません。<br/><br/>ユーザーが ASP.NET Web アプリケーションまたは ASP.NET Core Web アプリケーションを作成すると、リソースは .suo ファイルに保存されます。 ユーザーは Visual Studio 2015、Visual Studio 2017、または Visual Studio 2019 Preview でプロジェクトを開くことができます。両方のバージョンで使用されているプロジェクトとソリューションが Visual Studio でサポートされている限り、それぞれでリソース情報が使用されます。 ユーザーは製品ごとに 1 回認証する必要があります。 たとえば、Visual Studio 2017 で作成されたプロジェクトを Visual Studio 2019 Preview で開く場合、Visual Studio 2019 Preview で認証が要求されます。 |
| C#/Visual Basic Webform または Windows フォーム | プロジェクトは、Visual Studio 2019 Preview、Visual Studio 2017、および Visual Studio 2015 で開くことができます。 |
| コード化された UI テスト | UI 駆動型機能テストの自動化のためにコード化された UI テストは、Visual Studio 2019 Preview では非推奨になりました。 <br/><br/>Visual Studio 2019 は、コード化された UI テストの最後のリリースとなります。 Web アプリのテストには Selenium を使用し、デスクトップと UWP アプリのテストには Appium と WinAppDriver を一緒に使用することをお勧めします。 |
| データベース単体テスト プロジェクト (csproj、.vbproj) | 古いデータ単体テスト プロジェクトは Visual Studio 2019 Preview で読み込まれますが、依存関係は GAC に保存されているものが使用されます。 単体テスト プロジェクトをアップグレードし、最新の依存関係を使用するには、ソリューション エクスプローラーでプロジェクトを右クリックし、**[SQL Server 単体テスト プロジェクトに変換する]** を選択します。 |
| F# | Visual Studio 2019 Preview では、Visual Studio 2013、Visual Studio 2015、Visual Studio 2017 で作成されたプロジェクトを開くことができます。 新しいプロジェクトの以前の Visual Studio テンプレートとの主な違いは、FSharp.Core のバージョンが常に NuGet パッケージになったことです。 F# は任意の .NET ワークロードにより既定でインストールされます。|
| InstallShield<br/>MSI のセットアップ | Visual Studio 2010 で作成されたインストーラー プロジェクトは、[Visual Studio Installer Projects の拡張機能](https://marketplace.visualstudio.com/items?itemName=UnniRavindranathan-MSFT.MicrosoftVisualStudio2013InstallerProjects)を使って以降のバージョンで開くことができます。 「[WiX Toolset Visual Studio 2017 Extension](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)」も参照してください。 InstallShield Limited Edition は、Visual Studio に付属しなくなりました。 Visual Studio 2019 Preview で利用可能かどうかについては、[Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) にご確認ください。 |
| LightSwitch | LightSwitch は Visual Studio 2019 Preview または Visual Studio 2017 ではサポートされていません。 Visual Studio 2012 以前のバージョンで作成されたプロジェクトを Visual Studio 2013 または Visual Studio 2015 で開くとアップグレードされ、以後、Visual Studio 2013 または Visual Studio 2015 のみで開けるようになります。 |
| ロード テスト | Visual Studio 2019 Preview では、Web パフォーマンスとロード テストの機能は非推奨となっています。 <br/><br/>Visual Studio 2019 は、ロード テストの最後のリリースとなります。 Apache JMeter、Akamai CloudTest、Blazemeter など、代替のロード テスト ツールを使用してください。  |
| Microsoft Azure Tools for Visual Studio | これらの種類のプロジェクトを開くには、最初に [Azure SDK for .NET](http://azure.microsoft.com/downloads/)をインストールした後、プロジェクトを開きます。 必要に応じて、プロジェクトが更新されます。 |
| Microsoft Test Manager | Microsoft Test Manager と Feedback Client は、Visual Studio 2019 Preview からは Visual Studio に付属しません。 <br/><br/>手動テストまたは探索的テストの必要がある場合は、Azure Test Plans (Azure DevOps の一部) をご利用ください。 詳細については、ここを参照してください。 |
| モデル ビュー コントローラー フレームワーク (ASP.NET MVC) | MVC バージョンと Visual Studio のサポート:<ul><li>Visual Studio 2010 SP1 は MVC 2 と MVC 3 をサポートしています。MVC 4 サポートは [ASP.NET 4 MVC 4 for Visual Studio 2010 SP1 をダウンロード](https://www.microsoft.com/download/details.aspx?id=30683)すると追加されます。</li><li>Visual Studio 2012 は MVC 3 と MVC 4 のみをサポートしています。</li><li>Visual Studio 2013 は MVC 4 と MVC 5 のみをサポートしています。</li><li>Visual Studio 2019 Preview、Visual Studio 2017、および Visual Studio 2015 は MVC 4 (既存のオブジェクトを開くことはできますが、新規作成はできません) と MVC 5 をサポートしています。</li></ul><br/>MVC バージョンをアップグレードする:<ul><li>MVC 2 から MVC 3 に自動的にアップグレードする方法については、「[ASP.NET MVC 3 Application Upgrader](http://go.microsoft.com/fwlink/?LinkID=238178)」 (ASP.NET MVC 3 アプリケーション アップグレード プログラム) を参照してください。</li><li>MVC 2 から MVC 3 に手動でアップグレードする方法については、「 [Upgrading an ASP.NET MVC 2 Project to ASP.NET MVC 3 Tools Update (ASP.NET MVC 2 プロジェクトから ASP.NET MVC 3 Tools Update へのアップグレード)](http://go.microsoft.com/fwlink/?linkid=238178)」を参照してください。</li><li>MVC 3 から MVC 4 に手動でアップグレードする方法については、「 [Upgrading an ASP.NET MVC 3 Project to ASP.NET MVC 4 (ASP.NET MVC 3 プロジェクトから ASP.NET MVC 4 へのアップグレード)](http://www.asp.net/whitepapers/mvc4-release-notes)」を参照してください。 .NET Framework 3.5 SP1 を対象とするプロジェクトの場合は、.NET Framework 4 を使用するようにプロジェクトの対象を変更する必要があります。</li><li>MVC 4 から MVC 5 に手動でアップグレードする方法については、「[How to Upgrade an ASP.NET MVC 4 and Web API Project to ASP.NET MVC 5 and Web API 2](https://www.asp.net/mvc/overview/releases/how-to-upgrade-an-aspnet-mvc-4-and-web-api-project-to-aspnet-mvc-5-and-web-api-2) (ASP.NET MVC 4 と Web API プロジェクトを ASP.NET MVC 5 と Web API 2 にアップグレードする方法)」を参照してください。</li></ul> |
| モデリング | Visual Studio でプロジェクトを自動的に更新することを許可した場合は、Visual Studio 2015、Visual Studio 2013、または Visual Studio 2012 で開くことができます。<br/><br/>モデリング プロジェクトの形式は Visual Studio 2015 以来変わっていません。プロジェクトはこれらのバージョンで開いて変更することができます。 ただし、Visual Studio 2017 と Visual Studio 2019 Preview では動作に違いがあります。<ul><li>メニューとテンプレートで、モデリング プロジェクトの名称が "依存関係の検証" になりました。</li><li>UML 図は Visual Studio 2017 および Visual Studio 2019 Preview ではサポートされていません。 UML ファイルは以前と同様にソリューション エクスプローラーに一覧表示されますが、XML ファイルが開きます。 UML 図を表示、作成、編集するには、Visual Studio 2015 を使用してください。</li><li>Visual Studio 2019 Preview では、モデリング プロジェクトが構築されるとき、アーキテクチャの依存関係検証がなくなりました。 代わりに、コード プロジェクトが構築されるときに検証が実行されます。 この変更がモデリング プロジェクトに影響を与えることはありませんが、検証されるコード プロジェクトを変更する必要があります。 Visual Studio 2019 Preview では、コード プロジェクトを必要に応じて自動的に変更できます。</li></ul> |
| MSI セットアップ (vdproj) | InstallShield プロジェクトをご覧ください。 |
| Office 2007 VSTO | Visual Studio 2019 Preview への一方向のアップグレードが必要です。 |
| Office 2010 VSTO | .NET Framework 4 を対象とするプロジェクトの場合は、Visual Studio 2010 SP1 以降でこのプロジェクトを開くことができます。 他のすべてのプロジェクトは、一方向のアップグレードが必要です。 |
| ポータブル クラス ライブラリ (PCL) | ポータブル クラス ライブラリ (PCL) はサポートされなくなりました。 Visual Studio 2019 Preview では引き続き PCL を開いたりビルドできますが、新しい PCL プロジェクトを作成することはできません。 PCL プロジェクトのコードを .NET Standard プロジェクトに移行することをお勧めします。<br/><br/>PCL のサポートは既定では含まれなくなりますが、Visual Studio の "個々のコンポーネント" タブでは使用できます。 |
| Python ワークロード | Python Windows IoT Core アプリのサポートは、Visual Studio 2019 Preview で削除されました。 Visual Studio 2019 Preview にはこれに相当するものがないため、これらのプロジェクトへの自動移行パスはありません。<br/><br/>Visual Studio 2017 を引き続き使用することができます。 |
| R Tools for Visual Studio | R Tools for Visual Studio は、Visual Studio 2019 Preview でデータ サイエンス ワークロードから削除されました。<br/><br/>Visual Studio 2017 または RStudio などの代替手段を引き続き使用することができます。 |
| Service Fabric (sfproj) | Service Fabric アプリケーション プロジェクトが ASP.NET Core サービス プロジェクトを参照していない限り、Service Fabric アプリケーション プロジェクトは Visual Studio 2015、Visual Studio 2017、Visual Studio 2019 Preview のいずれかで開くことができます。 Visual Studio 2017 または Visual Studio 2019 Preview で開かれている Visual Studio 2015 からの Service Fabric プロジェクトは、xproj 形式から csproj への一方向の移行が行われます。 この表で前述した「.NET Core プロジェクト (xproj)」を参照してください。 |
| SharePoint 2010 | SharePoint ソリューション プロジェクトを Visual Studio 2019 Preview で開くと、SharePoint 2013 または SharePoint 2016 にアップグレードされます。 アップグレードのためには、".NET デスクトップ開発" ワークロードを Visual Studio 2019 Preview にインストールする必要があります。<br/><br/>SharePoint プロジェクトのアップグレード方法について詳しくは、「[SharePoint 2013 へのアップグレード](https://technet.microsoft.com/library/cc303420.aspx)」、「[SharePoint Server 2013 でワークフローを更新する](https://technet.microsoft.com/library/dn133867.aspx)」、および「[データベース接続アップグレード用の SharePoint Server 2016 ファームを作成する](https://technet.microsoft.com/library/cc263026(v=office.16).aspx)」をご覧ください。 |
| SharePoint 2016 | Office Developer Tools Preview 2 で作成された SharePoint アドイン プロジェクトを Visual Studio 2019 Preview で開くことはできません。 この制限を回避するには、csproj vbproj ファイルで、`MinimumVisualStudioVersion` を 12.0 に、`MinimumOfficeToolsVersion` を 12.2 に更新する必要があります。 |
| Silverlight | Silverlight プロジェクトは Visual Studio 2019 Preview ではサポートされていません。 Silverlight アプリケーションを維持するには、引き続き Visual Studio 2015 を使用してください。 |
| SQL - Redgate | Redgate の SQL Change Automation Core (旧称、ReadyRoll Core)、SQL Prompt Core、および SQL Search は、Visual Studio インストーラーに付属されななくなりました。<br/><br/>これらの機能には、Visual Studio 2017 を引き続き使用することができます。 Visual Studio 2019 Preview では、Redgate の SQL Toolbelt で入手可能な有料の SQL Change Automation および SQL Prompt 製品にアップグレードすることができます。|
| SQL Server Reporting Services および SQL Server Analysis Services (SSRS、SSDT、SSAS、MSAS) | これらのプロジェクト タイプのサポートは、Visual Studio ギャラリーの次の 2 つの拡張機能を通じて提供されます。[Microsoft Analysis Services Modeling Projects](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects) と [Microsoft Reporting Services Projects](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio)。 Visual Studio 2019 Preview のデータの保存と処理のワークロードには SSDT のサポートも含まれます。 |
| SQL Server Integration Services (SSIS) | Visual Studio 2019 Preview のサポートは、SQL Server Data Tools (SSDT) から使用できます。 詳細については、[SQL Server Integration Services のブログ](https://blogs.msdn.microsoft.com/ssis/2017/08/23/ssis-designer-is-now-available-for-visual-studio-2017/)をご覧ください。 |
| Visual C++ | Visual Studio 2019 Preview を使用して、Visual Studio 2010 以降の Visual Studio で作成されたプロジェクトを操作できます。 プロジェクトを初めて開いたときに、最新のコンパイラとツールセットにアップグレードするか、元のプロジェクトを引き続き使用するかを選択できます。 元のプロジェクトを引き続き使用することを選択した場合、Visual Studio 2019 Preview はプロジェクト ファイルを変更せず、以前の Visual Studio のインストールのツールセットを使用してプロジェクトをビルドします。 元のオプションを維持すると、必要に応じて、Visual Studio の元のバージョンでプロジェクトを開くことができます。 詳細については、「[Visual Studio でネイティブ マルチ ターゲットを利用し、古いプロジェクトを作成する](/cpp/porting/use-native-multi-targeting)」を参照してください。 |
| Visual Studio 拡張性/VSIX | MinimumVersion 14.0 以前のプロジェクトは、MinimumVersion 15.0 を宣言するように更新されます。この宣言により、前のバージョンの Visual Studio でプロジェクトを開けなくなります。 前のバージョンでプロジェクトを開くには、MinimumVersion を `$(VisualStudioVersion)` に設定します。 「[How to:Migrate Extensibility Projects to Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)」 (方法: 機能拡張プロジェクトを Visual Studio 2017 に移行する) もご覧ください。 |
| Visual Studio Lab Management | Microsoft Test Manager または Visual Studio 2010 SP1 以降を利用し、これらのバージョンで差制された環境を開くことができます。 ただし、Visual Studio 2010 SP1 の場合、環境を作成するには、使用している Microsoft Test Manager のバージョンが Team Foundation Server のバージョンと一致する必要があります。 |
| Visual Studio Tools for Apache Cordova | Apache Cordova のサポートは、Visual Studio 2019 Preview で削除されました。 Visual Studio 2019 Preview にはこれに相当するものがないため、これらのプロジェクトへの自動移行パスはありません。<br/><br/>Cordova Tools for Visual Studio Code 拡張機能 (Cordova の最新バージョンのサポートを提供) を使用することも、Visual Studio 2017 を引き続き使用することもできます。 |
| Web 配置 (wdproj) | 発行プロファイルのサポートが追加されたことで、Visual Studio 2012 では Web 配置プロジェクトのサポートが削除されました。 Visual Studio 2019 Preview にはこれに相当するものがないため、これらのプロジェクトへの自動移行パスはありません。 そこで、[StackOverflow](https://stackoverflow.com/a/12061065/1203388) に説明されているように、テキスト エディターで wdproj ファイルを開き、pubxml (発行プロファイル) ファイルに任意のカスタマイズをコピーおよび貼り付けます。 [Web サイトおよび Web 配置プロジェクトに関する計画](https://blogs.msdn.microsoft.com/webdev/2012/08/06/plans-regarding-website-projects-and-web-deployment-projects/)に関するページも参照してください。 |
| Windows Communication Foundation、Windows Workflow Foundation | このプロジェクトは、Visual Studio 2019 Preview、Visual Studio 2017、Visual Studio 2015、Visual Studio 2013、Visual Studio 2012 で開くことができます。 |
| Windows Presentation Foundation | このプロジェクトは、Visual Studio 2017、Visual Studio 2013、Visual Studio 2012、Visual Studio 2010 SP1 で開くことができます。 |
| Windows Phone アプリ | Windows Phone のプロジェクトは、Visual Studio 2019 Preview ではサポートされていません。 <br/><br/>Windows Phone 8.x アプリを維持するには、Visual Studio 2015 を使用してください。 Windows Phone 7.x プロジェクトを維持するには、Visual Studio 2012 を使用してください。 |
| Windows ストア アプリ | JavaScript ユニバーサル Windows プロジェクトは、Visual Studio 2019 Preview ではサポートされていません。 これらのプロジェクトを維持するには、Visual Studio 2017 を使用してください。 <br/><br/>Windows 10 Fall Creators Update (ビルド 16299) より前の Windows 10 SDK は、Visual Studio 2019 Preview インストーラーから削除されました。 古い SDK を手動でダウンロードすることも、新しい SDK を使用するようにプロジェクトを再ターゲットすることもできます。<br/><br/>project.json を使用しているユニバーサル Windows プロジェクトはサポートされていません。 パッケージ参照を使用するようにこれらのプロジェクトをアップグレードすることをお勧めします。 または、project.json ファイルで Microsoft.NET.Test.Sdk バージョン 16.0.0.0 への参照を追加します。<br/><br/>Windows Phone 8.1 および 8.0 のプロジェクトは、Visual Studio 2019 Preview ではサポートされていません。 これらのアプリを維持するには、引き続き Visual Studio 2015 を使用してください。 |
| Xamarin | Visual Studio および Visual Studio for Mac の Xamarin Live Player 拡張機能は削除されました。 これにより、ペアリングの画面とすべての統合が削除されます。 代わりに、Xamarin.Forms Previewer でビルドを使用してください。<br/><br/>Visual Studio Emulator for Android は、Visual Studio インストーラーから削除されました。 代わりに、Google Android エミュレーターで新しい HYPER-V サポートを使用してください。 |

## <a name="how-visual-studio-decides-when-to-migrate-a-project"></a>Visual Studio がプロジェクトを移行するタイミングを決定する方法

Visual Studio の各新規バージョンでは、一般に、バージョンが異なっても同じプロジェクトを開き、変更し、ビルドできるように、以前のバージョンとの互換性が維持されます。 ただし、時間の経過と共に、一部のプロジェクトの種類のサポート終了など、避けられない変更が発生します (Visual Studio 2019 Prevew でサポートされているプロジェクトの種類については、「[Visual Studio 2019 Preview の対象プラットフォームと互換性](/visualstudio/releases/2019/compatibility)」をご覧ください)。このような場合、新しいバージョンの Visual Studio はプロジェクトを読み込まず、移行パスを提供しません。そのようなプロジェクトは、それをサポートしている以前のバージョンの Visual Studio で管理する必要があります。

つまり、新しいバージョンの Visual Studio ではプロジェクトを開くことはできますが、以前のバージョンとの互換性がなくなる可能性がある方法でプロジェクトを更新または移行する必要があります。 Visual Studio は、複数の条件を使って、このような移行が必要かどうかを判断します。

- Visual Studio 2013 RTM まで遡る、プラットフォームのターゲット バージョンとの互換性。

- 以前のバージョンの Visual Studio との、デザイン時資産の互換性 (つまり、さまざまなチャネルの Visual Studio 2019 Preview、Visual Studio 2017、Visual Studio 2015 RTM & Update 3、Visual Studio 2013 RTM & Update 5、Visual Studio 2012 Update 4、Visual Studio 2010 SP 1)。Visual Studio 2019 Preview は、以前のバージョンでプロジェクトをまだ開くことができるように、非推奨のデザイン時資産を、破壊することなく正常に失敗させます。

- 新しいデザイン時資産により、Visual Studio 2013 RTM & Update 5 までの以前のバージョンとの互換性がなくなるかどうか。

対象のプロジェクトの種類のエンジニアリング所有者は、これらの条件を調べて、サポート、互換性、移行に関して問題があるときは問い合わせます。 ここでも、Visual Studio は、可能であれば Visual Studio のバージョン間の透過的な互換性を維持します。つまり、Visual Studio のあるバージョンで作成および変更したプロジェクトは、他のバージョンでもそのままで動作します。

ただし、この記事で説明されている一部のプロジェクトの種類のように、このような互換性が不可能な場合は、Visual Studio はアップグレード ウィザードを開いて必要な一方向の変更を行います。

このような一方向の変更には、プロジェクト ファイルでの `ToolsVersion` プロパティの変更が含まれます。これは、最終的に必要な実行可能で配置可能なアーティファクトにプロジェクトのソース コードを変換できる MSBuild の正確なバージョンを示します。 つまり、プロジェクトと以前のバージョンの Visual Studio との互換性を損なうものは、*Visual Studio* のバージョンではなく、`ToolsVersion` によって決定される *MSBuild* のバージョンです。 お使いの Visual Studio のバージョンに、プロジェクトでの `ToolsVersion` と一致する MSBuild ツールチェーンが含まれている限り、Visual Studio をそのツールチェーンを呼び出してプロジェクトをビルドできます。

以前のバージョンで作成されたプロジェクトとの最大限の互換性を維持するため、Visual Studio 2019 Preview には、`ToolsVersion` 15、14、12、4 をサポートするために必要な MSBuild ツールチェーンが含まれています。 これらの `ToolsVersion` 値のいずれかを使うプロジェクトでは、ビルドが成功するはずです (やはり、「[Visual Studio 2019 Preview の対象プラットフォームと互換性](/visualstudio/releases/2019/compatibility)」で説明されているように、Visual Studio 2017 がプロジェクトの種類をサポートするかどうかに依存します)。

このコンテキストでの必然的な疑問は、新しい `ToolsVersion` 値にプロジェクトを手動で更新または移行する必要があるかどうかということです。 そのような変更は不要であり、行うと、修正するにはプロジェクトの再ビルドが必要な多くのエラーと警告が発生する可能性があります。 さらに、将来 Visual Studio が特定の `ToolsVersion` をサポートしなくなった場合、プロジェクトを開くと、`ToolsVersion` の値を変更する必要があるため、プロジェクト移行プロセスが開始されます。 そのような場合、その特定のプロジェクトの種類のサブシステムは、変更が必要なものを正確に知っており、この記事で前述したように自動的にこれらの変更を行うことができます。

## <a name="next-steps"></a>次の手順

詳しくは、次の記事をご覧ください。

- [ToolsVersion ガイダンス](../msbuild/msbuild-toolset-toolsversion.md)
- [フレームワーク対象設定機能ガイダンス](../ide/visual-studio-multi-targeting-overview.md)

## <a name="see-also"></a>関連項目

[Visual Studio 2017 のプロジェクトの移行とアップグレードのリファレンス](port-migrate-and-upgrade-visual-studio-projects.md)