---
title: 管理者として実行
ms.date: 06/05/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2c581797c36cfd69032ef635a9944b339333d6de
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684679"
---
# <a name="user-permissions-and-visual-studio"></a>ユーザー アクセス許可と Visual Studio

セキュリティ上の理由により、Visual Studio はできる限り通常のユーザーとして実行してください。

> [!WARNING]
> また、信頼できる人または信頼できる場所以外から入手した Visual Studio ソリューションをコンパイル、起動、またはデバッグしないでください。

Visual Studio IDE のほぼすべての機能は、通常のユーザーとして実行できます。 次のタスクを完了するには、管理者アクセス許可が必要です。

|区分|タスク|詳細情報|
|----------|----------| - |
|インストール|Visual Studio をインストールする。|[Visual Studio のインストール](../install/install-visual-studio.md)|
||ローカル ヘルプ コンテンツをインストール、更新、または削除する。|[ローカル ヘルプ コンテンツのインストールと管理](../help-viewer/install-manage-local-content.md)|
|ツールボックス|**ツールボックス**にクラシック COM コントロールを追加する。|[ツールボックス](../ide/reference/toolbox.md)|
|ビルド|コンポーネントを登録するビルド後のイベントを使用する。|[カスタム ビルド ステップとビルド イベントについて](/cpp/ide/understanding-custom-build-steps-and-build-events)|
||C++ プロジェクトのビルド時に登録手順を含める。||
|デバッグ|昇格されたアクセス許可で実行されたアプリケーションをデバッグする。|[デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)|
||ASP.NET Web サイトなど、別のユーザー アカウントで実行されたアプリケーションをデバッグする。|[ASP.NET アプリケーションおよび AJAX アプリケーションのデバッグ](../debugger/how-to-enable-debugging-for-aspnet-applications.md)|
||XAML ブラウザー アプリケーション (XBAP) をゾーンでデバッグする。|[WPF ホスト (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||エミュレーターを使用して、Microsoft Azure クラウド サービス プロジェクトをデバッグする。|[Visual Studio でのクラウド サービスのデバッグ](/azure/vs-azure-tools-debug-cloud-services-virtual-machines)|
||リモート デバッグ用にファイアウォールを構成する。|[リモート デバッグ](../debugger/remote-debugging.md)|
|パフォーマンス ツール|アプリケーションをプロファイルする。|[パフォーマンス プロファイリングのビギナーズ ガイド](../profiling/beginners-guide-to-performance-profiling.md)|
|配置|ローカル コンピューターでインターネット インフォメーション サービス (IIS) に Web アプリケーションを配置する。|[Visual Studio を使用して ASP.NET Core Web アプリを配置する](/aspnet/web-forms/overview/older-versions-getting-started/deployment-to-a-hosting-provider/)|

## <a name="run-visual-studio-as-an-administrator"></a>Visual Studio を管理者として実行する

Visual Studio を管理者として実行する必要がある場合は、次の手順に従って IDE を開きます。

> [!NOTE]
> ここで説明する手順は Windows 10 用です。 これらの手順は、Windows のその他のバージョンの場合と似ています。

1. **[スタート]** メニューを開き、Visual Studio 2017 にスクロールします。

1. 右クリックして、つまり **Visual Studio 2017** のコンテキスト メニューから **[その他]** > **[管理者として実行]** を選択します。

   Visual Studio の起動時には、**[(管理者)]** がタイトル バーの製品名の後に表示されます。

アプリケーションのショートカットを変更して、常に管理者アクセス許可で実行することもできます。

## <a name="see-also"></a>関連項目

- [Visual Studio プロジェクトのポート、移行、アップグレード](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Visual Studio のインストール](../install/install-visual-studio.md)