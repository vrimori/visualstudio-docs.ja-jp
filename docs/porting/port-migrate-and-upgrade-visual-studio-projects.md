---
title: "Visual Studio プロジェクトのポート、移行、アップグレード | Microsoft Docs"
ms.custom: 
ms.date: 2/27/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: dac3cb1d7767c2ff76ac25f6a486ad30a8d54831
ms.openlocfilehash: 6b61cbc8460266ac305b12bf14f92d7445bfc900
ms.lasthandoff: 03/03/2017

---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Visual Studio プロジェクトのポート、移行、アップグレード

通常、新しいバージョンの Visual Studio はいずれも、以前の種類のプロジェクト、ファイル、その他のアセットに対応しています。 それらのオブジェクトはこれまでと同様に操作できます。新しい機能を利用していない場合でも、Visual Studio 2015、Visual Studio 2013、Visual Studio 2012 など、以前のバージョンとの下位互換性が維持されています。 (どの機能がどのバージョンに固有の機能であるかについては、[リリース ノート](https://www.visualstudio.com/vs/release-notes/)を参照してください。)

ただし、今後変更される場合もあります。 新しいバージョンの Visual Studio では、特定の種類のサポートが終了しています。あるいは、下位互換性がないので、移行や更新が要求されます。 このトピックでは、Visual Studio 2017 で影響を受ける種類のプロジェクトについて説明します。 Visual Studio 2017 でサポートされている種類の一覧は「[対象プラットフォームと互換性](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs)」というトピックにあります。

> [!Note]
> 特定の種類のプロジェクトを開くとき、Visual Studio インストーラーで適切なワークロードを追加する必要があります。


## <a name="projects"></a>プロジェクト

次の一覧は、Visual Studio 2017 より前のバージョンで作成されたプロジェクトに対する Visual Studio 2017 でのサポートをまとめたものです。 表示されるはずのプロジェクトまたはファイルの種類が見つからない場合、[このトピックの Visual Studio 2015 バージョン](https://msdn.microsoft.com/library/hh266747.aspx)を調べ、下のコメントにメモしてください。

| プロジェクトの種類 | サポート |
| --- | --- |
| .NET Core プロジェクト (.xproj) | Visual Studio 2015 で作成したプロジェクトでは、.xproj プロジェクト ファイルが含まれるプレビュー ツールが使用されていました。 Visual Studio 2017 で .xproj ファイルを開くと、ファイルを .csproj 形式に移行するように求められます (.xproj ファイルのバックアップが作成されます)。 .NET Core プロジェクトのこの .csproj 形式は、VS2015 以前のバージョンではサポートされていません。  .xproj 形式は .csproj に移行しなければ Visual Studio 2017 で利用できません。 |
| ASP.NET Web アプリケーションと ASP.NET Core Web アプリケーション (Application Insights が有効) | Visual Studio のユーザーごとのリソース情報がユーザー インスタンス別にレジストリに保存されます。 これは、プロジェクトを開いていない状態で Azure Application Insights データを検索するときに利用されます。 Visual Studio 2015 では、Visual Studio 2017 とは異なるレジストリの場所が使用され、競合しません。<br/><br/>ユーザーが ASP.NET Web アプリケーションまたは ASP.NET Core Web アプリケーションを作成すると、リソースは .suo ファイルに保存されます。 ユーザーは Visual Studio 2015 や 2017 でプロジェクトを開くことができます。両方のバージョンで使用されているプロジェクトとソリューションが Visual Studio でサポートされている限り、両方でリソース情報が使用されます。 ユーザーは製品ごとに&1; 回認証する必要があります。 たとえば、Visual Studio 2015 で作成されたプロジェクトを Visual Studio 2017 で開く場合、Visual Studio 2017 で認証が要求されます。 |
| C#/Visual Basic Webform または Windows フォーム | プロジェクトを Visual Studio 2017 と Visual Studio 2015 で開くことができます。 |
| データベース単体テスト プロジェクト (.csproj、.vbproj)    | 古いデータ単体テスト プロジェクトは Visual Studio 2017 で読み込まれますが、依存関係は GAC に保存されているものが使用されます。 単体テスト プロジェクトをアップグレードし、最新の依存関係を使用するには、ソリューション エクスプローラーでプロジェクトを右クリックし、**[SQL Server 単体テスト プロジェクトに変換する]** を選択します。 |
| F# | Visual Studio 2017 では、Visual Studio 2013 と 2015 で作成したプロジェクトを開くことができます。 ただし、これらのプロジェクトで Visual Studio 2017 機能を有効にするには、プロジェクトのプロパティを開き、ターゲットの fsharp.core を F# 4.1 に変更します。 |
| LightSwitch | LightSwitch は Visual Studio 2017 ではサポートされていません。 Visual Studio 2012 以前のバージョンで作成されたプロジェクトを Visual Studio 2013 または Visual Studio 2015 で開くとアップグレードされ、以後、Visual Studio 2013 または Visual Studio 2015 のみで開けるようになります。 |
| Microsoft Azure Tools for Visual Studio | これらの種類のプロジェクトを開くには、最初に [Azure SDK for .NET](http://azure.microsoft.com/en-us/downloads/)をインストールした後、プロジェクトを開きます。 必要に応じて、プロジェクトが更新されます。 |
| モデル ビュー コントローラー フレームワーク (ASP.NET MVC) | MVC バージョンと Visual Studio のサポート:<ul><li>Visual Studio 2010 SP1 は MVC 2 と MVC 3 をサポートしています。MVC 4 サポートは [ASP.NET 4 MVC 4 for Visual Studio 2010 SP1 をダウンロード](https://www.microsoft.com/en-us/download/details.aspx?id=30683)すると追加されます。</li><li>Visual Studio 2012 は MVC 3 と MVC 4 のみをサポートしています。</li><li>Visual Studio 2013 は MVC 4 と MVC 5 のみをサポートしています。</li><li>Visual Studio 2017 と Visual Studio 2015 は MVC 4 (既存のオブジェクトを開くことはできますが、新規作成はできません) と MVC 5 をサポートしています。</li></ul><br/><br/>MVC バージョンをアップグレードする:<ul><li>MVC 2 から MCV 3 に自動的にアップグレードする方法については、「 [ASP.NET MVC 3 Application Upgrader (ASP.NET MVC 3 アプリケーション アップグレード プログラム)](http://go.microsoft.com/fwlink/?LinkID=238178)」を参照してください。</li><li>MVC 2 から MVC 3 に手動でアップグレードする方法については、「 [Upgrading an ASP.NET MVC 2 Project to ASP.NET MVC 3 Tools Update (ASP.NET MVC 2 プロジェクトから ASP.NET MVC 3 Tools Update へのアップグレード)](http://go.microsoft.com/fwlink/?linkid=238178)」を参照してください。</li><li>MVC 3 から MVC 4 に手動でアップグレードする方法については、「 [Upgrading an ASP.NET MVC 3 Project to ASP.NET MVC 4 (ASP.NET MVC 3 プロジェクトから ASP.NET MVC 4 へのアップグレード)](http://www.asp.net/whitepapers/mvc4-release-notes)」を参照してください。 .NET Framework 3.5 SP1 を対象とするプロジェクトの場合は、.NET Framework 4 を使用するようにプロジェクトの対象を変更する必要があります。</li><li>MVC 4 から MVC 5 に手動でアップグレードする方法については、「[How to Upgrade an ASP.NET MVC 4 and Web API Project to ASP.NET MVC 5 and Web API 2](https://www.asp.net/mvc/overview/releases/how-to-upgrade-an-aspnet-mvc-4-and-web-api-project-to-aspnet-mvc-5-and-web-api-2) (ASP.NET MVC 4 と Web API プロジェクトを ASP.NET MVC 5 と Web API 2 にアップグレードする方法)」を参照してください。</li></ul> |
| モデリング | Visual Studio でプロジェクトを自動的に更新することを許可した場合は、Visual Studio 2015、Visual Studio 2013、または Visual Studio 2012 で開くことができます。<br/><br/>モデリング プロジェクトの形式は Visual Studio 2015 と Visual Studio 2017 の間で変わっていません。プロジェクトはいずれのバージョンでも開き、変更できます。 ただし、Visual Studio 2017 では動作に違いがあります。<ul><li>メニューとテンプレートで、モデリング プロジェクトの名称が “依存関係の検証” になりました。</li><li>UML 図は Visual Studio 2017 ではサポートされていません。 UML ファイルは以前と同様にソリューション エクスプローラーに一覧表示されますが、XML ファイルが開きます。 UML 図を表示、作成、編集するには、Visual Studio 2015 を使用してください。</li><li>Visual Studio 2017 では、モデリング プロジェクトが構築されるとき、アーキテクチャの依存関係検証がなくなりました。 代わりに、コード プロジェクトが構築されるときに検証が実行されます。 この変更がモデリング プロジェクトに影響を与えることはありませんが、検証されるコード プロジェクトを変更する必要があります。 Visual Studio 2017 では、コード プロジェクトを必要に応じて自動的に変更できます ([詳細](http://go.microsoft.com/fwlink/?LinkId=827800))。</li></ul> |
| Silverlight | Silverlight プロジェクトは Visual Studio 2017 ではサポートされていません。 Silverlight アプリケーションを維持するには、引き続き Visual Studio 2015 を使用してください。 |
| Visual C++ | Visual Studio 2015 で作成したソリューションやプロジェクトを Visual Studio 2017 でそのまま利用できますが、それより古いバージョンの Visual Studio で作成されたプロジェクトの場合、プロジェクトのアップグレードが要求されたり、Visual Studio 2017 で構築するためにそのバージョンより新しいツールセットにターゲットを変更することが要求されたりすることがあります。 詳細については、「[方法: Visual C++ プロジェクトを Visual Studio 2015 にアップグレードする](https://msdn.microsoft.com/en-us/library/hh690665.aspx)」と「[Visual C++ 移植とアップグレードのガイド](https://msdn.microsoft.com/en-us/library/dn986839.aspx)」を参照してください。 |
| Visual Studio 拡張性/VSIX | MinimumVersion 14.0 以前のプロジェクトは、MinimumVersion 15.0 を宣言するように更新されます。この宣言により、前のバージョンの Visual Studio でプロジェクトを開けなくなります。 前のバージョンでプロジェクトを開くには、MinimumVersion を `$(VisualStudioVersion)` に設定します。 「[How to: Migrate Extensibility Projects to Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)」 (方法: 機能拡張プロジェクトの Visual Studio 2017 への移行) も参照してください。 |
| Visual Studio Lab Management | Microsoft Test Manager または Visual Studio 2010 SP1 以降を利用し、これらのバージョンで差制された環境を開くことができます。 ただし、Visual Studio 2010 SP1 の場合、環境を作成するには、使用している Microsoft Test Manager のバージョンが Team Foundation Server のバージョンと一致する必要があります。 |
| Visual Studio Tools for Apache Cordova |このプロジェクトは Visual Studio 2017 で開くことができますが、下位互換性はありません。 Visual Studio 2015 からプロジェクトを開くと、プロジェクトを変更するように求められます。 `taco.json` ファイルの代わりにツールセットを利用し、Cordova ライブラリのバージョン、そのプラットフォームとプラグイン、そのノード/npm 依存関係を管理するようにプロジェクトがアップグレードされます。 詳細については、[移行ガイド](http://taco.visualstudio.com/docs/vs-taco-2017-migration/)を参照してください。 |
| Windows Communication Foundation、Windows Workflow Foundation | このプロジェクトは、Visual Studio 2017、Visual Studio 2015、Visual Studio 2013、Visual Studio 2012 で開くことができます。 |
| Windows Presentation Foundation | このプロジェクトは、Visual Studio 2013、Visual Studio 2012、Visual Studio 2010 SP1 で開くことができます。 |
| Windows ストア/フォン アプリ | Visual Studio 2017 では、Windows Store 8.1 と 8.0 または Windows Phone 8.1 と 8.0 のプロジェクトはサポートされていません。 これらのアプリを維持するには、引き続き Visual Studio 2015 を使用してください。 Windows Phone 7.x プロジェクトを維持するには、Visual Studio 2012 を使用してください。 |
