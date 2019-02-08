---
title: エラー :Web サーバーが正しく構成されていない |Microsoft Docs
ms.date: 09/20/2017
ms.topic: troubleshooting
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd59211da9228f2940c675f889d0536fbea9045d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55019193"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>エラー :Web サーバーは正しく構成されていません。

ここで説明するには、問題を解決する手順を実行した後と、デバッグをもう一度試す前に IIS をリセットする必要もあります。 管理者のコマンド プロンプトを開き、入力を行うことができます`iisreset`します。

この問題を解決するのには次の手順を実行するには。

1. リリース ビルドでは、デバッグ ビルドとしてを再発行し、web.config ファイルが含まれていることを確認として、サーバーでホストされている web アプリが構成されている場合`debug=true`compilation 要素にします。 IIS と再試行をリセットします。

    たとえば、リリース ビルドを発行プロファイルを使用している場合デバッグに変更し、再発行します。 Debug 属性に設定する場合は、`false`を発行するとします。

2. (IIS)物理パスが正しいことを確認します。 IIS では、この設定でを検索する**基本設定 > 物理パス**(または**詳細設定**古いバージョンの IIS で)。

    Web アプリケーションが別のコンピューターにコピーされる、手動での名前変更または移動する場合に物理パスを正しいできない可能性があります。 IIS と再試行をリセットします。

3. Visual Studio でローカルでデバッグいる場合は、プロパティで正しいサーバーが選択されていることを確認します。 (開いている**プロパティ > Web > サーバー**または**プロパティ > デバッグ**プロジェクトの種類によって異なります。 Web フォーム プロジェクトを開く**プロパティ ページ > オプションの開始 > サーバー**)。

    IIS などの外部の (カスタム) サーバーを使用している場合、URL が正しくなければなりません。 それ以外の場合、IIS Express と [再試行] を選択します。

4. (IIS)正しいバージョンの ASP.NET がサーバーにインストールされていることを確認します。

    Visual Studio プロジェクトと IIS で ASP.NET のバージョンの不一致には、この問題が発生します。 Web.config で、フレームワークのバージョンを設定する必要があります。IIS で ASP.NET をインストールするには、使用、 [Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)します。 またを参照してください[IIS 8.0 を使用して ASP.NET 3.5 および ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)または ASP.NET Core, [IIS と Windows 上のホスト](https://docs.asp.net/en/latest/publishing/iis.html)します。
  
4. 場合、 `maxConnection` IIS での制限が小さすぎる、接続が多すぎますがあるとする必要があります、[接続制限を増やす](/iis/configuration/system.applicationhost/sites/sitedefaults/limits)します。
  
## <a name="see-also"></a>関連項目
 [リモートの IIS コンピューター上の ASP.NET のリモート デバッグ](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)   
 [Web アプリケーションのデバッグ: エラーとトラブルシューティング](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
