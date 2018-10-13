---
title: 移植、移行、および Visual Studio プロジェクトのアップグレード |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
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
caps.latest.revision: 108
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: ec590e3c643f731a9c85bc59c0c36394988f6c7c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204257"
---
# <a name="porting-migrating-and-upgrading-visual-studio-projects"></a>Porting, Migrating, and Upgrading Visual Studio Projects
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 の最新ドキュメントについては、次を参照してください。[ポート、移行、および Visual Studio プロジェクトのアップグレード](https://docs.microsoft.com/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)します。

Visual Studio の新しいバージョンに移行するかどうかを考慮する場合は、このドキュメントを使用して、 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 、または Visual Studio 2010 SP1 で作成したソリューション、プロジェクト、ファイル、および他のアセットのうち、どれが [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] および [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]で変更することなく実行できるかを確認できます。 または、Visual Studio のバージョンでサポートされていないプロジェクトを開こうとしてエラー メッセージが表示された場合、またはAzure SDK for .NET などの SDK または拡張機能が必要な場合に、このページが表示されることもあります。  
  
 広く使用されている多くの資産は、 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]、 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 、およびそれより前の 2 つのバージョンと同様の方法で動作します。 たとえば、[!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] では、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] または [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] で作成したプロジェクトを開いて変更を加え、[!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] で再度開くことができます。変更結果は持続し、プロジェクトは以前のバージョンと同じ方法で動作します。 これは、Visual Studio 2010 SP1 で作成した多くの資産にも当てはまります。  
  
 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] を [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、またはVisual Studio 2010 SP1 と共に使用する場合は、これらのバージョンのいずれでも、プロジェクトとファイルを作成および変更できます。 いずれかのバージョンでサポートされていない機能を追加しない限り、バージョン間でプロジェクトとファイルを移行できます。  
  
##  <a name="project"></a> プロジェクト  
 次の一覧は、 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] または Visual Studio 2010 SP1 で作成したプロジェクトの [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] または [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] におけるサポートについての説明です。 この一覧を使用して、[!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、または Visual Studio 2010 SP1 でそのままの状態でプロジェクトを開くことができるか、または互換性を確保するために変更する必要があるかを確認できます。  
  
|プロジェクトの種類|互換性|  
|---------------------|-------------------|  
|ユニバーサル Windows プラットフォーム アプリ|ユニバーサル Windows アプリ用ツールをインストールするには、Visual Studio のセットアップで **[カスタム]** または **[変更]** を選択し、 **[ユニバーサル Windows アプリ開発ツール]** を選択します。<br /><br /> Windows 10 向けのユニバーサル Windows プラットフォーム (UWP) アプリの開発は、Windows 10 または [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] の [!INCLUDE[win81](../includes/win81-md.md)]でのみサポートされています。|  
|Windows ストア アプリ|Windows 8.1 と Windows Phone 8.1 の両方を対象とするユニバーサル アプリを含む、Windows ストア アプリの開発は、 [!INCLUDE[win81](../includes/win81-md.md)] と Windows 10 でサポートされています。 既存の [!INCLUDE[win8](../includes/win8-md.md)] プロジェクトは引き続き使用できますが、新しい [!INCLUDE[win8](../includes/win8-md.md)] プロジェクトは作成できません。 [!INCLUDE[win81](../includes/win81-md.md)] プロジェクトは、特定の種類の参照のみに依存できます。 詳細については、「[プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)」を参照してください。 **注:** [!INCLUDE[win81](../includes/win81-md.md)]を使用して作成したプロジェクト[!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]または[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]で開くことができません[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]します。 これは、 [!INCLUDE[win81](../includes/win81-md.md)] または [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] を使用して作成した [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] プロジェクトがこれらのバージョンを対象とし、 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] は [!INCLUDE[win8](../includes/win8-md.md)] を対象とする [!INCLUDE[win8](../includes/win8-md.md)]プロジェクトのみをサポートしているためです。|  
|[!INCLUDE[net_v451](../includes/net-v451-md.md)]|適切なマルチ ターゲット パックをインストールした後で、 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] および [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] でこれらのプロジェクトを作成して使用することができます。 これらのプロジェクトは、Visual Studio 2010 SP1 ではサポートされていません。|  
|[!INCLUDE[net_v45](../includes/net-v45-md.md)]|これらのプロジェクトを [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]、 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 、および [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]で作成して開くことはできますが、Visual Studio 2010 SP1 では不可能です。|  
|BizTalk|BizTalk サーバー プロジェクトは、[!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] または [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] と互換性がありません。|  
|C#/Visual Basic Silverlight 4 アプリケーションまたはクラス ライブラリ|Visual Studio でプロジェクトを自動的に更新することを許可した場合は、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] または [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] のどちらかで開くことができます。|  
|C#/Visual Basic Webform または Windows フォーム|[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] および [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] でプロジェクトを開くことができます。|  
|Visual Basic 6 および Visual C++ 6|Visual Studio 2012 と [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] は、Visual Basic 6 または Visual C++ 6 でビルドされたアプリケーションのデバッグをサポートしていません。これらのアプリケーションをデバッグするには、以前のバージョンの Visual Studio を使用してください。|  
|コード化された UI テスト|Visual Studio でプロジェクトを自動的に更新することを許可した場合は、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、および Visual Studio 2010 SP1 で開くことができます。|  
|F#|Visual Studio 2010 SP1 で作成したプロジェクトを自動的にアップグレードすることを許可した場合は、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] と [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] で開くことができます。 ただし、Visual Studio の古いバージョンで作成された Silverlight プロジェクトを [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] にアップグレードすることはできません。 代わりに、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] で Silverlight プロジェクトを作成し、そのプロジェクトにコードをコピーする必要があります。 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] で作成した Silverlight プロジェクトは、Silverlight 5 を対象とします。|  
|LightSwitch|Visual Studio でプロジェクトを自動的にアップグレードすることを許可した場合は、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] でのみ開くことができます。|  
|ローカル データベース キャッシュ|**には、ローカル データベース キャッシュ テンプレートおよび** [データ同期の構成] [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]ダイアログ ボックスがありません。 Microsoft Synchronization Services v1.0 がインストールされている場合は、 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] を使用して、 [!INCLUDE[vs2010](../includes/vs2010-md.md)] で作成されたプロジェクトを開いて実行できます。ただし、 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]でそのプロジェクトを更新する場合は、コードを手動ですべて変更する必要があります。 代わりに、引き続き [!INCLUDE[vs2010](../includes/vs2010-md.md)] を使用して、これらのプロジェクトを管理および更新することもできます。  新たに開発する場合は、Microsoft Sync Framework によって提供される新しい同期モデルを対象とします。 詳細については、「 [Microsoft Sync Framework Developer Center (Microsoft Sync Framework デベロッパー センター)](http://msdn.microsoft.com/sync/default)」をご覧ください。|  
|モデル ビュー コントローラー フレームワーク|Visual Studio 2010 SP1 は MVC 2 と MVC 3 のみ、 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] は MVC 3 と MVC 4 のみ、および [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] は MVC 4 のみをサポートします。 MVC 2 から MCV 3 に自動的にアップグレードする方法については、「 [ASP.NET MVC 3 Application Upgrader (ASP.NET MVC 3 アプリケーション アップグレード プログラム)](http://go.microsoft.com/fwlink/?LinkID=238178)」を参照してください。 MVC 2 から MVC 3 に手動でアップグレードする方法については、「 [Upgrading an ASP.NET MVC 2 Project to ASP.NET MVC 3 Tools Update (ASP.NET MVC 2 プロジェクトから ASP.NET MVC 3 Tools Update へのアップグレード)](http://go.microsoft.com/fwlink/?linkid=238178)」を参照してください。 MVC 3 から MVC 4 に手動でアップグレードする方法については、「 [Upgrading an ASP.NET MVC 3 Project to ASP.NET MVC 4 (ASP.NET MVC 3 プロジェクトから ASP.NET MVC 4 へのアップグレード)](http://www.asp.net/whitepapers/mvc4-release-notes)」を参照してください。 .NET Framework 3.5 SP1 を対象とするプロジェクトの場合は、.NET Framework 4 を使用するようにプロジェクトの対象を変更する必要があります。|  
|モデリング|Visual Studio でプロジェクトを自動的に更新することを許可した場合は、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、または Visual Studio 2010 SP1 で開くことができます。<br /><br /> Team Foundation でモデリング プロジェクトをビルドすると、Team Foundation はプロジェクト内のレイヤーの検証を試みます。 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] では、Team Foundation ビルドは Visual Studio 2010 SP1 で作成されたモデリング プロジェクトに関するレイヤーを検証できません。 ただし、Visual Studio 2010 SP1 では、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] で作成されたモデリング プロジェクト内のレイヤーを検証できます。|  
|MPI/クラスター デバッガー|[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、または Visual Studio 2010 SP1 を実行しているコンピューターに同じバージョンのランタイムまたはツールがインストールされている場合は、3 つのバージョンすべてでこのプロジェクトを開くことができます。|  
|MSI セットアップ (.vdproj)|[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] では、このプロジェクトの種類がサポートされていないため、このプロジェクトを開くことができません。 ほとんどの Windows プラットフォームおよびアプリケーション ランタイムを直接サポートする無料の配置ソリューションである InstallShield Limited Edition for Visual Studio (ISLE) を使用することをお勧めします。 また、ISLE を使用して、Visual Studio インストーラー プロジェクトからデータと設定をインポートすることもできます。 で変更することなく実行できるかを確認できます。|  
|Office 2007 VSTO|プロジェクトをアップグレードして、Office 2013 と .NET Framework 4 を対象にすると、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、または Visual Studio 2010 SP1 でこのプロジェクトを開くことができます。|  
|Office 2010 VSTO|.NET Framework 4 を対象とするプロジェクトの場合は、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、および Visual Studio 2010 SP1 でこのプロジェクトを開くことができます。 他のすべてのプロジェクトは、一方向のアップグレードが必要です。|  
|リッチ インターネット アプリケーション|プロジェクトをアップグレードした後は、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、および Visual Studio 2010 SP1 で開くことができます。|  
|SharePoint 2007|[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] でこのプロジェクトを開くことはできません。 ただし、プロジェクトを SharePoint 2010 に手動でアップグレードすると、 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、および Visual Studio 2010 SP1 で開くことができます。 SharePoint 2007 にアップグレードする方法の詳細については、次を参照してください[IT プロフェッショナル向け SharePoint 2007 から SharePoint 2010 への移行](http://go.microsoft.com/fwlink/?LinkId=238224)、 [2007 ワークフローを Visual Studio & SharePoint 2010 に移行する](http://go.microsoft.com/fwlink/?LinkId=238225)、と。[SharePoint Server 2010 の SharePoint エンタープライズ検索移行ツール](http://go.microsoft.com/fwlink/?LinkId=238226)します。|  
|SharePoint 2010|プロジェクトを [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、および Visual Studio 2010 SP1 で開くことができます。|  
|SketchFlow|Visual Studio でプロジェクトを WPF 4.5/Silverlight 5 にアップグレードすることを許可した場合は、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] と [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] で開くことができます。|  
|[!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)] データベース|プロジェクトを [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、および Visual Studio 2010 SP1 で開くことができます。 SQL Server の以前のバージョンで作成されたデータベース ファイル (.mdf) がある場合は、SQL Server Express LocalDB でファイルを使用する前に [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] にアップグレードする必要があります。ただし、そのデータベースはもう、SQL Server の以前のバージョンとの互換性がなくなります。 アップグレードしない場合は、同じコンピューターに [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] をインストールして使用することで、 [!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)] でデータベースを引き続き使用できます。 詳細については、次を参照してください。 [.mdf ファイルをアップグレードする](../data-tools/upgrade-dot-mdf-files.md)します。|  
|[!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express|[!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)]、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、および Visual Studio 2010 SP1 を実行しているコンピューターに [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] Express がインストールされている場合は、3 つのバージョンすべてでプロジェクトを開くことができます。|  
|SQL Server レポート プロジェクト|[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] および [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] でプロジェクトを開くことができます。 ローカル モードの場合のみ (つまり、SQL Server に接続されていない場合)、 [!INCLUDE[vs2010](../includes/vs2010-md.md)]のビューアーに関連付けられているコントロールをデザイン時に操作することはできませんが、プロジェクトは実行時に適切に機能します。 **注意:** に固有の機能を追加する場合[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]レポート スキーマが自動的にアップグレードしでプロジェクトを開くことができなく、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]します。|  
|単体テスト|[!INCLUDE[TCMext](../includes/tcmext-md.md)]、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、および Visual Studio 2010 SP1 で [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] を使用して、これらのバージョンのいずれかで作成されたテストを開くことができます。|  
|Visual C++|[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] を使用して、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] または Visual Studio 2010 SP1 で作成された C++ プロジェクトを開くことができます。 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] ビルド環境を使用して、 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]で作成されたプロジェクトをビルドする場合は、同じコンピューターに両方のバージョンの Visual Studio をインストールする必要があります。 詳細については、「[方法: Visual C++ プロジェクトを Visual Studio 2015 にアップグレードする](../porting/how-to-upgrade-visual-cpp-projects-to-visual-studio-2015.md)」と「[Visual C++ 移植とアップグレードのガイド](http://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb)」を参照してください。|  
|Visual Studio 2010 Web|Visual Studio でプロジェクトを自動的にアップグレードすることを許可した場合は、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、および Visual Studio 2010 SP1 で開くことができます。|  
|Visual Studio 2010 データベース (.dbproj)|プロジェクトを SQL Server Data Tools Database プロジェクトに変換すると、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] で開くことができます。 ただし、 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] では、次の成果物をサポートしていません。<br /><br /> -単体テスト<br />-データ生成計画<br />-データ比較ファイル<br />-静的コード分析のためのカスタム ルール拡張機能<br />-ある server.sqlsettings<br />-.sqlcmd ファイル<br />-カスタム デプロイの拡張機能<br />-部分プロジェクト (.files)<br /><br /> SQL Server Data Tools をインストールすると、プロジェクトを変換した後に Visual Studio 2010 SP1 で開くことができます。 詳細については、「 [Microsoft SQL Server Data Tools](http://msdn.microsoft.com/data/tools.aspx)」を参照してください。|  
|Visual Studio 2010 Visual Database Tools|このプロジェクトを [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、および Visual Studio 2010 SP1 で開くことができます。|  
|Visual Studio Lab Management|[!INCLUDE[TCMext](../includes/tcmext-md.md)]、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、および Visual Studio 2010 SP1 で [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] を使用して、これらのバージョンのいずれかで作成された環境を開くことができます。 ただし、環境を作成するには、使用している Microsoft Test Manager のバージョンが Team Foundation Server のバージョンと一致する必要があります。|  
|Visual Studio マクロ|[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] では、プロジェクトの種類がサポートされていないため、このプロジェクトを開くことができません。|  
|Visual Studio SDK/VSIX|Visual Studio SDK プロジェクトを [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]にアップグレードした後は、 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]で開くことができません。 詳細については、次を参照してください。[方法: Visual Studio 2015 への機能拡張プロジェクトの移行](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)します。|  
|Microsoft Azure Tools for Visual Studio|Microsoft Azure Tools for Visual Studio Version 2.1 を使用している場合は、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、および Visual Studio 2010 SP1 でプロジェクトを開くことができます。 以前のバージョンを対象とするプロジェクトの場合、Visual Studio でプロジェクトを Version 2.1 にアップグレードすることを許可すると、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、および Visual Studio 2010 SP1 で開くことができます。|  
|Windows Communication Foundation、Windows Presentation Foundation|このプロジェクトを [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、および Visual Studio 2010 SP1 で開くことができます。|  
|Windows Mobile|[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] では、プロジェクトの種類がサポートされていないため、このプロジェクトを開くことができません。|  
|Windows Phone 7.1|Visual Studio でプロジェクトを Windows Phone 8.0 にアップグレードすることを許可した場合は、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] と [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] で開くことができます。|  
|その他|その他のほとんどのプロジェクトの種類は、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、および Visual Studio 2010 SP1 で開くことができます。|  
|FrontPage Web サイト|[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] では、プロジェクトの種類がサポートされていないため、このプロジェクトを開くことができません。|  
|ポータブル クラス ライブラリ|Visual Studio でプロジェクトを自動的に更新することを許可した場合は、 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、または Visual Studio 2010 SP1 で開くことができます。<br /><br /> -Silverlight 4 を対象とするプロジェクトには、Silverlight 5 を対象とします。<br />-Windows Phone 7.0 または Windows Phone 7.5 を対象とするプロジェクトでは、Windows Phone 8 を対象とします。<br />-Xbox 360 を対象とするプロジェクトでは、Xbox 360 を対象が不要になった。|  
|クラウド サービス プロジェクト (.ccproj 拡張子) などの Azure プロジェクト、および .deployproj 拡張子の Azure Resource Manager プロジェクト (クラウド配置プロジェクト)|これらの種類のプロジェクトを開くには、最初に [Azure SDK for .NET](http://azure.microsoft.com/en-us/downloads/)をインストールした後、プロジェクトを開きます。|  
  
## <a name="troubleshooting-project-compatibility-issues"></a>プロジェクトの互換性の問題のトラブルシューティング  
 ここでは、プロジェクトが [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] または [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]で開かない場合に実行できるいくつかの対処方法を示します。  
  
-   [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] または [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] でサポートされていないプロジェクトを開く場合、そのプロジェクトに関連付けられているバージョンの Visual Studio がインストールされていなければ、プロジェクトの種類がサポートされていないことを示すメッセージが表示されることがあります。その際、 **[プロジェクトとソリューションの変更をレビュー]** ダイアログ ボックスの **[サポートされていないプロジェクト]** の下にそのプロジェクトの種類が表示されることがあります。 この問題を解決するには、Windows の **コントロール パネル**を開き、 **[Visual Studio]**、 **[変更]**、 **[修復]** の順に選択します。 ここで、必要なバージョンをインストールできます。  
  
-   [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] でデスクトップ アプリのプロジェクトを開こうとすると、エラーが発生し、"このエディションの Visual Studio は、[!INCLUDE[win81](../includes/win81-md.md)] アプリのみをサポートします。" または "このプロジェクトは、Visual Studio の現在のエディションと互換性がありません。" というメッセージが表示されます。 [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] は、Windows 8.1 向けに設計された Windows ストア アプリの開発、テスト、展開用に制限されています。 デスクトップ アプリ プロジェクトを開くには、そのプロジェクトの種類をサポートしている Visual Studio のエディションを使用する必要があります。  
  
     Visual Studio のエディションに関する詳細については、「 [Microsoft Visual Studio Products (Microsoft Visual Studio 製品)](http://go.microsoft.com/fwlink/?LinkId=254332)」をご覧ください。  
  
-   [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop で Windows ストア アプリ プロジェクトを開こうとすると、エラーが発生します。 [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop を使用して Windows ストア アプリをビルドできません。 Windows ストア アプリをビルドするには、[!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] をインストールします。 または、Microsoft のすべてのプラットフォームと Web 用のアプリを開発するには、Visual Studio Professional 2013 を試してください。  
  
-   プロジェクトで [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] に固有の機能が必要な場合は、以前のバージョンでそのプロジェクトを開くことはできません。  
  
-   [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] を使用している場合に、 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]で作成されたプロジェクトを開くには、プロジェクト システムをカスタマイズして、 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]の機能を組み込む方法を使用できます。 これを行う方法については、次を参照してください。[を行うカスタム プロジェクト バージョンの認識](../misc/making-custom-projects-version-aware.md)します。  
  
 追加のトラブルシューティング情報については、サポート技術情報の「 ["Visual Studio 2013 Compatibility (Visual Studio 2013 の互換性)](http://support.microsoft.com/kb/2863286) 」を参照してください。  
  
##  <a name="file"></a> ファイル  
 次の一覧では、 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] で各ファイルの種類がサポートされているかどうか、 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] と Visual Studio 2010 SP1 でファイルを開くことができるかどうか、および互換性を保持するために変更を加える必要があるかどうかを確認できます。  
  
|ファイルの種類|互換性|  
|------------------|-------------------|  
|AppManifest、Inbrowsersettings、OutOfBrowserSettings (.xml ファイル)|これらのファイルは、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、および Visual Studio 2010 SP1 で開くことができます。|  
|BizTalk フラット ファイル スキーマ|[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] でこれらのスキーマを BizTalk 2013 プロジェクトに追加できます。 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] を、フラット ファイル スキーマを持つ BizTalk 2010 プロジェクトと組み合わせて使用するには、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] がインストールされているコンピューターに BizTalk 2013 をインストールします。 BizTalk 2010 プロジェクトを最初に開くときに、そのプロジェクトは自動的に BizTalk 2013 または [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] プロジェクト システムにアップグレードされます。|  
|クライアント レポート定義 (.rdlc) ファイル|これらのファイルは [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] で開くことができます。[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] の機能およびコントロールを追加すると、スキーマが自動的にアップグレードされます。|  
|コード分析規則セット|これらのファイルは、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、および Visual Studio 2010 SP1 で開くことができます。|  
|データ層アプリケーション パッケージ ファイル|これらのファイルは、Version 2.0 または Version 2.5 の場合、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] で開くことができます。|  
|デバッガー ダンプ ファイル|これらのファイルは、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、および Visual Studio 2010 SP1 で開くことができます。|  
|Directed Graph Markup Language (DGML) 図ファイル|これらのファイルは、変更せずに [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、および Visual Studio 2010 SP1 で開くことができます。|  
|エンティティ データ モデル (EDMX) ファイル|[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] では、ファイルを変更せずに、.NET Framework 4.5 または .NET Framework 4 を対象とする EDMX ファイルを開くことができます。|  
|プロファイラー レポート ファイル|プロファイラー レポート ファイル (.vsp、.vsps、.psess、および .vspf) は、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] と [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] で開くことができます。 .vspx ファイルを Visual Studio 2010 SP1 で開くことはできません。|  
|ソリューション (.suo) ファイル|[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] を使用して、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] または Visual Studio 2010 SP1 で作成されたソリューション ファイルを開くことができます。|  
|SQL Server Compact Edition|[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] では、SQL Server Compact エディションはサポートされていません。|  
|SQLX ファイル|[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] でこれらのファイルを開くには、一方向のアップグレードを実行し、Visual Studio の対象バージョンで .sqlx ファイルを配置した後、ファイルを .dacpac 形式でリビルドする必要があります。|  
|[!INCLUDE[vs2010](../includes/vs2010-md.md)] の IntelliTrace ログ ファイル|これらのファイルは、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、および Visual Studio 2010 SP1 で開くことができます。|  
|JavaScript メモリ アナライザー (.diagsession) ファイル|Visual Studio の旧バージョンで作成されたファイルを [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]で表示できます。 ただし、収集した情報によっては、 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] で作成されたファイルを [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] または Visual Studio 2010 SP1 で開くことができない場合があります。|  
  
##  <a name="integration"></a> 統合資産  
 Visual Studio Team Foundation Server の異なるバージョンのクライアントおよびサーバーを使用する場合は、互換性の問題が発生する可能性があります。  
  
|統合の種類|互換性|  
|-------------------------|-------------------|  
|コード レビューおよび担当作業|[!INCLUDE[esprfound](../includes/esprfound-md.md)] クライアントを [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)] に接続した場合は、コード レビュー機能および担当作業機能を使用できません。|  
|[!INCLUDE[vs_dev11_expwin_long](../includes/vs-dev11-expwin-long-md.md)]|MSBuild や [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] などの 64 ビット環境を使用して、 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] で作成した [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)]アプリをビルドすることはできません。|  
  
## <a name="see-also"></a>関連項目  
 [カスタム プロジェクトでのバージョンの認識](../misc/making-custom-projects-version-aware.md)



