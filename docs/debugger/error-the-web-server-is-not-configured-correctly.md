---
title: "エラー: web サーバーが正しく構成されていません |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/20/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.remote.projnotconfigured
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: debugger, Web application errors
ms.assetid: 875ba87f-c372-4126-8fe3-e33931cf26c0
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0538693a815cf9749b3cd9df007486de1af3637
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>エラー : Web サーバーは正しく構成されていません。

問題を解決するのにはここで詳細な手順を行った後、デバッグを再試行する前に、IIS をリセットする必要もあります。 管理者コマンド プロンプトを開き、」と入力して実行できます`iisreset`です。

この問題を解決するのには次の手順を実行します。

1. として、サーバーでホストされている web アプリが構成されている場合、リリース ビルドは、デバッグ ビルドでとして再発行し、web.config ファイルが含まれていることを確認`debug=true`compilation 要素にします。 IIS と再試行をリセットします。

    たとえば、リリース ビルドで、公開プロファイルを使用している場合デバッグに変更し、再発行します。 それ以外の場合、デバッグ属性に設定する`false`をパブリッシュする場合。

2. (IIS)物理パスが正しいことを確認します。 IIS でこの設定を検索する**基本設定 > 物理パス**(または**詳細設定**古いバージョンの IIS で)。

    Web アプリケーションが、別のコンピューターにコピー、手動での名前を変更または移動する場合に物理パスを正しいできない可能性があります。 IIS と再試行をリセットします。

3. Visual Studio で、プロパティで、適切なサーバーが選択されていることを確認します。 (開いている**プロパティ > Web > サーバー**または**プロパティ > デバッグ**プロジェクトの種類によって異なります。 Web フォームは、プロジェクトを開く**プロパティ ページ > 開始オプション > サーバー**)。

    IIS などの外部 (カスタム) サーバーを使用している場合、URL が正しい場合があります。 それ以外の場合、IIS Express と [再試行] を選択します。

4. (IIS)サーバーの正しいバージョンの ASP.NET がインストールされていることを確認します。

    Visual Studio プロジェクトと IIS で ASP.NET のバージョンが一致しないには、この問題が発生します。 Web.config のフレームワークのバージョンを設定する必要があります。IIS で ASP.NET をインストールするには、使用、 [Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)です。 またを参照してください[IIS 8.0 を使用して ASP.NET 3.5 と ASP.NET 4.5](https://docs.microsoft.com/en-us/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)または ASP.NET Core [IIS と Windows 上のホスト](https://docs.asp.net/en/latest/publishing/iis.html)です。
  
4. 場合、 `maxConnection` IIS での制限が低すぎると接続が多すぎますがある、する必要があります[接続制限を増やす](https://docs.microsoft.com/en-us/iis/configuration/system.applicationhost/sites/sitedefaults/limits)です。
  
## <a name="see-also"></a>関連項目  
 [ASP.NET の IIS のリモート コンピューター上でリモート デバッグ](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)   
 [Web アプリケーションのデバッグ : エラーおよびトラブルシューティング](../debugger/debugging-web-applications-errors-and-troubleshooting.md)