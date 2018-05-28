---
title: ユーザー アクセス許可と Visual Studio
ms.date: 11/04/2016
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
ms.openlocfilehash: 08b12e09348a28276d0c5d2f375b26e75c1ac3c5
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="user-permissions-and-visual-studio"></a>ユーザー アクセス許可と Visual Studio

セキュリティ上の理由により、Visual Studio はできる限り通常のユーザーとして実行してください。

> [!WARNING]
> また、信頼できる人または信頼できる場所以外から入手した Visual Studio ソリューションをコンパイル、起動、またはデバッグしないでください。

通常のユーザーでも Visual Studio IDE のほぼすべてのタスクを実行できますが、次のタスクを実行するには管理者のアクセス許可が必要です。

|区分|タスク|詳細情報|
|----------|----------|--------------------------|
|インストール|Visual Studio をインストールする。|[Visual Studio のインストール](../install/install-visual-studio.md)|
||ローカル ヘルプ コンテンツをインストール、更新、または削除する。|[ローカル コンテンツのインストールと管理](../ide/install-and-manage-local-content.md)|
|アプリケーションの種類|SharePoint のソリューションを開発する。|[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)|  
||[!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] の開発者ライセンスを取得する。|[開発者ライセンスを取得](http://go.microsoft.com/fwlink/?LinkID=241313)|
|ツールボックス|**ツールボックス**にクラシック COM コントロールを追加する。|[ツールボックス](../ide/reference/toolbox.md)|
|アドイン|IDE でクラシック COM を使用して記述されたアドインをインストールおよび使用する。|[アドインとウィザードを作成する](http://msdn.microsoft.com/Library/c5a47c21-6668-4de3-898d-afa969317e73)|
|ビルド|コンポーネントを登録するビルド後のイベントを使用する。|[カスタム ビルド ステップとビルド イベントについて](/cpp/ide/understanding-custom-build-steps-and-build-events)|
||C++ プロジェクトのビルド時に登録手順を含める。|[カスタム ビルド ステップとビルド イベントについて](/cpp/ide/understanding-custom-build-steps-and-build-events)|
|デバッグ|昇格されたアクセス許可で実行されたアプリケーションをデバッグする。|[デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)|
||ASP.NET Web サイトなど、別のユーザー アカウントで実行されたアプリケーションをデバッグする。|[ASP.NET アプリケーションおよび AJAX アプリケーションのデバッグ](../debugger/debugging-aspnet-and-ajax-applications.md)|
||XAML ブラウザー アプリケーション (XBAP) をゾーンでデバッグする。|[WPF ホスト (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||エミュレーターを使用して、Microsoft Azure クラウド サービス プロジェクトをデバッグする。|[Visual Studio でのクラウド サービスのデバッグ](http://go.microsoft.com/fwlink/?LinkId=266725)|
||リモート デバッグのファイアウォールを構成する。|[リモート デバッグ](../debugger/remote-debugging.md)|
|パフォーマンス ツール|アプリケーションをプロファイルする。|[パフォーマンス プロファイリングのビギナーズ ガイド](../profiling/beginners-guide-to-performance-profiling.md)|
|配置|ローカル コンピューターでインターネット インフォメーション サービス (IIS) に Web アプリケーションを配置する。|[Visual Studio または Visual Web Developer を使用しているホスティング プロバイダーへの ASP.NET Web アプリケーションの配置: テスト環境としての IIS への配置](http://go.microsoft.com/fwlink/?LinkId=266478)|
>>>>>>> 346075117af3d2bd1fddd9c3aca24516a39fa6a3

## <a name="run-visual-studio-as-an-administrator"></a>Visual Studio を管理者として実行する

IDE を起動するたびに管理アクセス許可を使用して Visual Studio を起動するか、管理アクセス許可で常に実行するようにアプリケーション ショートカットを変更できます。 詳細については、Windows のヘルプを参照してください。

### <a name="run-visual-studio-with-administrative-permissions"></a>管理アクセス許可を使用して Visual Studio を実行する

ここで説明する手順は Windows 10 用です。 これらの手順は、Windows のその他のバージョンの場合と似ています。

1. **[スタート]** メニューを開き、Visual Studio 2017 にスクロールします。

1. 右クリックして、つまり **Visual Studio 2017** のコンテキスト メニューから **[その他]** > **[管理者として実行]** を選択します。

     Visual Studio の起動時には、**[(管理者)]** がタイトル バーの製品名の後に表示されます。

## <a name="see-also"></a>関連項目

- [Visual Studio プロジェクトのポート、移行、アップグレード](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Visual Studio のインストール](../install/install-visual-studio.md)