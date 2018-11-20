---
title: ファイアウォールまたはプロキシ サーバーの内側に Visual Studio for Mac をインストールして使用する
description: このドキュメントでは、企業環境で Visual Studio for Mac (および Xamarin などのワークロード) が機能するように、ファイアウォールでホワイトリストに登録する必要があるホストのリストを示します。
ms.topic: troubleshooting
ms.assetid: 79C0F1A3-0C13-4E55-A820-1138A4082B77
author: asb3993
ms.author: amburns
ms.date: 10/23/2018
ms.openlocfilehash: 70ac8defdcea9cccd8a3b3f9be71d38fb78c9c50
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295196"
---
# <a name="install-and-use-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>ファイアウォールまたはプロキシ サーバーの内側に Visual Studio for Mac をインストールして使用する

ユーザーまたはユーザーの組織でファイアウォールやプロキシ サーバーなどのセキュリティ対策を講じている場合は、Visual Studio for Mac および Azure Services をインストールして使用するときに最適なエクスペリエンスを得るために、"ホワイトリスト" への登録をお勧めするドメイン URL および開くことをお勧めするポートおよびプロトコルがあります。

- [**Visual Studio for Mac のインストール**](#install-visual-studio-for-mac): これらの表には、Visual Studio for Mac の機能およびワークロードにアクセスできるようにするために、ホワイトリストに登録すべき URL を示します。

- [**Visual Studio for Mac の使用**](#use-visual-studio-for-mac): これらの表には、目的のサービスと機能のすべてにアクセスできるホワイトリストの URL が含まれています。

## <a name="install-visual-studio-for-mac"></a>Visual Studio for Mac をインストールする

Visual Studio for Mac インストーラーはさまざまなドメイン サーバーとダウンロード サーバーからダウンロードされるため、構成で信頼できるものとして追加することができるドメインと URL を次に示します。

### <a name="microsoft-domains"></a>Microsoft ドメイン

| ドメイン| 目的 |
| ----------------------------------- |---------------------------|
| *.live.com| 資格情報の管理 |
| app.vssps.visualstudio.com| インストーラーのメタデータ|
| vortex.data.microsoft.com | クラッシュとエラー報告 |
| az667904.vo.msecnd.net| クラッシュとエラー報告 |
| xamarin.com | インストーラーのメタデータ|
| xampubdl.blob.core.windows.net| インストーラー パッケージ|
| download.visualstudio.microsoft.com | インストーラー パッケージ|
| xamarin.azureedge.net | インストーラー パッケージ|
| developer.xamarin.com | インストーラー パッケージ|
| dc.services.visualstudio.com| クラッシュ レポート |

### <a name="third-party-domains"></a>サード パーティ ドメイン

| ドメイン| 目的 |
| --------------------------|-------------------------|
| dl.google.com | Android SDK |
| download.oracle.com | Java SDK|
| api.apple-cloudkit.com| Azure セキュリティ サービス |

## <a name="use-visual-studio-for-mac"></a>Visual Studio for Mac の使用

プロキシまたはファイアウォールの背後に配置し、Visual Studio for Mac の必要なすべての機能にアクセスできるようにするには、以下のドメインとポートをホワイトリストに登録することをお勧めします。

### <a name="general"></a>全般

| ドメイン | ポート|目的|
| ----------------------|------------------|------------------|
| go.microsoft.com | 80/443|Microsoft URL の解決 |
| vsstartpage.blob.core.windows.net| 80/443| スタート ページ データ|
| software.xamarin.com |  80/443|Updater サービス|
| addins.monodevelop.com | 80/443| 拡張機能サービス |
| visualstudio-devdiv-c2s.msedge.net | 80/443| 実験的な機能と通知 |
| targetednotifications.azurewebsites.net|  80/443| 通知のグローバル リストを、特定の種類のコンピューター/使用状況シナリオにのみ適用されるリストへとフィルター処理するために使用されます。|

### <a name="identity"></a>同一。

| ドメイン | ポート|目的|
| ----------------------|------------------|------------------|
| login.microsoftonline.com | 80/443| ID プロバイダー|
| secure.aadcdn.microsoftonline-p.com | 80/443|ID プロバイダー|
| dc.services.visualstudio.com| 80/443|クラッシュ レポート|
| management.azure.com|80/443| Azure サービス API |

### <a name="nuget"></a>NuGet

| ドメイン | ポート|目的|
| ----------------------|------------------|------------------|
| api.nuget.org | 80/443|NuGet API|
| secure.aadcdn.microsoftonline-p.com |80/443| ID プロバイダー|

### <a name="android-projects"></a>Android プロジェクト

| ドメイン| 目的|
| ------------------------------------|------------------------------------|
| time.android.com| Android Emulator 用タイム サーバー |
| connectivitycheck.gstatic.com | Android Emulator の接続|
| cloudconfig.googleapis.com| Android Emulator の API|

## <a name="see-also"></a>関連項目

- [ファイアウォールまたはプロキシ サーバーの内側に Visual Studio 2017 および Azure Services をインストールして使用する](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server)
- [Windows に関する同様の問題のトラブルシューティング](/visualstudio/install/troubleshooting-network-related-errors-in-visual-studio)
