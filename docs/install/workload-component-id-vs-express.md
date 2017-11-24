---
title: "Visual Studio Desktop Express 2017 のワークロード ID とコンポーネント ID | Microsoft Docs"
description: "ワークロードとコンポーネント ID は、コマンド ラインを使用して Visual Studio をインストールするか、または VSIX マニフェストで依存関係として指定するために使用します"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 10/09/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: 
ms.technology:
- vs-ide-install
- vs-ide-sdk
ms.assetid: a3c0cc76-e3ce-435c-a1af-a6318b5a4dbe
ms.openlocfilehash: 7a69153f0df6ba6f7da19f5e2a0046209fffdaf6
ms.sourcegitcommit: 2c7f48ad6073a81fa927568793633f26cc1f0b15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="visual-studio-desktop-express-2017-workload-and-component-ids"></a>Visual Studio Desktop Express 2017 のワークロード ID とコンポーネント ID

このページの表では、コマンド ラインを使用して Visual Studio をインストールするか、VSIX マニフェストで依存関係として指定するために使用できる ID の一覧を示します。 Visual Studio の更新プログラムがリリースされる際には、さらにコンポーネントが追加される予定です。

また、このページに関して以下の点に注意してください。

* 各ワークロードに個別のセクションがあり、ワークロード ID と、そのワークロードで利用できるコンポーネントの表が示されています。
* 既定では、ワークロードをインストールすると**必須**コンポーネントがインストールされます。 選択した場合は、**推奨**コンポーネントと**オプション** コンポーネントもインストールできます。
* どのワークロードにも関連付けられていない追加のコンポーネントの一覧を示したセクションも追加しました。

VSIX マニフェストで依存関係を設定するときは、コンポーネント ID のみを指定する必要があります。 このページの表を使用して、コンポーネントの最小の依存関係を確認してください。 シナリオによって、1 つのワークロードの 1 つのコンポーネントだけを指定する場合もあれば、 1 つのワークロードの複数のコンポーネントを指定したり、複数のワークロードの複数のコンポーネントを指定したりする場合もあります。 詳しくは、「[How to: Migrate Extensibility Projects to Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)」 (機能拡張プロジェクトを Visual Studio 2017 に移行する方法) をご覧ください。

これらの ID の使用方法の詳細については、「[Use Command-Line Parameters to Install Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)」(コマンドライン パラメーターを使用して Visual Studio 2017 をインストールする) をご覧ください。 他の製品のワークロードとコンポーネント ID の一覧については、「[Visual Studio 2017 Workload and Component IDs](workload-and-component-ids.md)」(Visual Studio 2017 のワークロードとコンポーネント ID) をご覧ください。

## <a name="express-for-windows-desktop"></a>Express for Windows Desktop

**ID:** Microsoft.VisualStudio.Workload.WDExpress

**説明:** 構文認識コード編集、ソース コード管理、作業項目管理を備える WPF、WinForms、Win32 などのネイティブおよびマネージ アプリケーションのビルド。 C#、Visual Basic、Visual C++ のサポートが含まれます。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Microsoft.Component.ClickOnce | ClickOnce Publishing | 15.0.26919.1 | 必須
Microsoft.Component.HelpViewer | ヘルプ ビューアー | 15.0.26711.1 | 必須
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | 必須
Microsoft.Component.VC.Runtime.OSSupport | UWP 用の Visual C++ ランタイム | 15.0.26621.2 | 必須
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.0.26621.2 | 必須
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.0.26621.2 | 必須
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.0.26621.2 | 必須
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | 必須
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26621.2 | 必須
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.0.26621.2 | 必須
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.0.26621.2 | 必須
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 15.0.26606.0 | 必須
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開発ツール | 15.0.26606.0 | 必須
Microsoft.VisualStudio.Component.Common.Azure.Tools | 接続および発行ツール | 1.10.50614.2 | 必須
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio のコア エディター | 15.0.26606.0 | 必須
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 Tools | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.NuGet | NuGet パッケージ マネージャー | 15.0.26621.2 | 必須
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 15.0.26711.1 | 必須
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL ランタイム | 15.0.26606.0 | 必須
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server の CLR データ型 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server コマンド ライン ユーティリティ | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server サポートのためのデータ ソース | 15.0.26621.2 | 必須
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26919.1 | 必須
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26906.1 | 必須
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.TextTemplating | テキスト テンプレート変換 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.VC.CLI.Support | C++/CLI サポート | 15.0.26823.1 | 必須
Microsoft.VisualStudio.Component.VC.Tools.ARM | ARM 用 Visual C++ コンパイラとライブラリ | 15.0.26906.1 | 必須
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | ARM64 用 Visual C++ コンパイラとライブラリ | 15.0.26906.1 | 必須
Microsoft.VisualStudio.Component.VisualStudioData | データソースとサービス参照 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | デスクトップ用 Windows 10 SDK (10.0.16299.0) C++ [x86 および x64] | 15.0.27004.2002 | 必須
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | デスクトップ用 Windows 10 SDK (10.0.16299.0) C++ [ARM および ARM64] | 15.0.27004.2002 | 必須
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | UWP 用 Windows 10 SDK (10.0.16299.0): C#、VB、JS | 15.0.27004.2002 | 必須
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | UWP 用 Windows 10 SDK (10.0.16299.0): C++ | 15.0.27004.2002 | 必須

## <a name="unaffiliated-components"></a>関連付けられていないコンポーネント

以下のコンポーネントはどのワークロードにも含まれていませんが、個別のコンポーネントとして選択できます。

コンポーネント ID | 名前 | バージョン
--- | --- | ---
適用なし | 該当なし | 適用なし

## <a name="get-support"></a>サポートを受ける
ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング](troubleshooting-installation-issues.md)」ページにあるトラブルシューティングのヒントをご覧ください。 また、Visual Studio IDE の [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから製品の問題を Microsoft に報告していただくことや、[UserVoice](https://visualstudio.uservoice.com/forums/121579) でご提案を共有していただくこともできます。 [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、質問したり、回答を検索したりできます。 [Gitter コミュニティの Visual Studio に関する意見交換](https://gitter.im/Microsoft/VisualStudio) ([GitHub](https://github.com/) アカウントが必要) から、Microsoft や他の Visual Studio 開発者と情報を交換することもできます。

## <a name="see-also"></a>関連項目

* [Visual Studio のワークロードとコンポーネント ID](workload-and-component-ids.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
  * [コマンド ライン パラメーターの例](command-line-parameter-examples.md)
* [Visual Studio のオフライン インストールを作成する](create-an-offline-installation-of-visual-studio.md)
