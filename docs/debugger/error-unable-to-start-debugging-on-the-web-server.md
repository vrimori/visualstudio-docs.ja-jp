---
title: "エラー: Web サーバーでデバッグを開始できません |。Microsoft ドキュメント"
ms.custom: 
ms.date: 05/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, debugging DLLs
- debugger, Web application errors
- unable to start debugging error
- security [debugger], Web applications
- debugging [Visual Studio], errors
- HTTP servers, debugging error
- security settings, checking for default Web sites
- errors [debugger], unable to start debugging
- debugging ASP.NET Web applications, unable to start debugging error
- remote debugging, errors
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a7d09deda1aa2b24fba90f9d9d417917c5b284ad
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2018
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>エラー ： Web サーバーでデバッグを開始できません

Web サーバーで実行されている ASP.NET アプリケーションをデバッグしようとすると、このエラー メッセージが表示する可能性があります:`Unable to start debugging on the Web server`です。

多くの場合、アプリケーション プール、IIS をリセット、またはその両方に更新が必要なエラーまたは構成の変更が発生したため、このエラーが発生します。 管理者特権でコマンド プロンプトを開く」と入力し、IIS をリセットできます`iisreset`です。 

## <a name="specificerrors"></a>詳細なエラー メッセージとは何ですか。

`Unable to start debugging on the Web server`メッセージはジェネリックです。 通常、詳細メッセージがエラーの文字列に含まれ、可能性がありますより正確な修正プログラムの検索、問題の原因を特定します。 次より一般的なエラー メッセージをメインのエラー メッセージに追加されたいくつかを示します。

- [IIS での起動に一致する web サイトが表示されない url](#IISlist)
- [Web サーバーが正しく構成されていません](#web_server_config)
- [Web サーバーに接続できません。](#unabletoconnect)
- [Web サーバーは、適切なタイミングで反応しませんでした。](#webservertimeout)
- [Microsoft visual studio リモート デバッグ monitor(msvsmon.exe) がないが、リモート コンピューターで実行されています。](#msvsmon)
- [リモート サーバーがエラーを返しました](#server_error)
- [ASP.NET のデバッグを開始できませんでした。](#aspnet)
- [デバッガーがリモート コンピューターに接続できません。](#cannot_connect)
- [表示については、一般的な構成エラーです。デバッガーの外で web ページを実行している可能性があります詳細情報を提供します。](#see_help)

## <a name="IISlist"></a>IIS での起動に一致する web サイトが表示されない url

- 管理者として Visual Studio を再起動して、デバッグを再試行してください。 (一部 ASP.NET のデバッグ シナリオには、高度な特権が必要があります)。

    常に、Visual Studio のショートカット アイコンを右クリックして、管理者として実行する Visual Studio を構成することができますを選択する**プロパティ > [詳細設定]**、し、常に管理者として実行を選択します。

## <a name="web_server_config"></a>Web サーバーが正しく構成されていません

- 参照してください[エラー: web サーバーが正しく構成されていない](../debugger/error-the-web-server-is-not-configured-correctly.md)です。

## <a name="unabletoconnect"></a>Web サーバーに接続できません。

- Visual Studio と Web サーバーを同じコンピューターで実行されているを使用したデバッグ**f5 キーを押して**(の代わりに**プロセスにアタッチする**)? プロジェクトのプロパティを開きを適切な Web サーバーに接続し、URL を起動して、プロジェクトが構成されていることを確認します。 (開いている**プロパティ > Web > サーバー**または**プロパティ > デバッグ**プロジェクトの種類によって異なります。 Web フォームは、プロジェクトを開く**プロパティ ページ > 開始オプション > サーバー**)。

- それ以外の場合、アプリケーション プールを再起動し、IIS をリセットします。 詳細については、次を参照してください。 [IIS 構成を調べて](#vxtbshttpservererrorsthingstocheck)です。

## <a name="webservertimeout"></a>Web サーバーは、適切なタイミングで反応しませんでした。

- IIS をリセットして、デバッグを再試行してください。 デバッガーの複数のインスタンスが接続されて、IIS プロセスです。リセットは終了します。 詳細については、次を参照してください。 [IIS 構成を調べて](#vxtbshttpservererrorsthingstocheck)です。

## <a name="msvsmon"></a>Microsoft visual studio リモート デバッグ monitor(msvsmon.exe) がないが、リモート コンピューターで実行されています。

- リモート コンピューターでデバッグする場合があることを確認[インストールされ、リモート デバッガーを実行している](../debugger/remote-debugging.md)です。 メッセージには、ファイアウォールが特記しています場合、確認、[ファイアウォールでポートを解決](../debugger/remote-debugger-port-assignments.md)が開いて、サードパーティ製のファイアウォールを使用している場合に特にです。
- HOSTS ファイルを使用している場合は、正しく構成されていることを確認してください。 たとえばを使用したデバッグ**f5 キーを押して**(の代わりに**プロセスにアタッチする**)、ホスト ファイルをプロジェクトのプロパティと同様に、同じプロジェクト URL を含める必要があります**プロパティ > Web > サーバー**または**プロパティ > デバッグ**プロジェクトの種類によって異なります。

## <a name="server_error"></a>リモート サーバーがエラーを返しました

問題の原因を識別できるように、メッセージで返されるエラー コードを確認します。 ここでは、いくつかの一般的なエラー コードです。
- (403) 許可されていません。 正しいサーバーの種類と URL に接続していることを確認してください (で**プロパティ > Web > サーバー**または**プロパティ > デバッグ**プロジェクトの種類に応じて、)。 また、サーバーの web.config に含まれていることを確認`debug=true`compilation 要素にします。 これらの設定は既に修正いる場合は、Web アプリケーションのフォルダーが正しいフォルダーの権限を持っていることを確認します。 詳細については、次を参照してください。 [IIS 構成を調べて](#vxtbshttpservererrorsthingstocheck)です。
- (503) サーバーは利用できません。 アプリケーション プールを停止して、エラーまたは構成の変更により可能性があります。 アプリケーション プールを再起動します。
- (404) not Found です。 ASP.NET の正しいバージョンのアプリケーション プールが構成されていることを確認します。

## <a name="aspnet"></a>ASP.NET のデバッグを開始できませんでした。

- アプリケーション プールを再起動し、IIS をリセットします。 詳細については、次を参照してください。 [IIS 構成を調べて](#vxtbshttpservererrorsthingstocheck)です。
- URL 書き換えを行う場合は、基本の web.config でない URL 書き換えをテストします。 参照してください、**注**URL に関する内のモジュールを書き直してください。 [IIS 構成を調べて](#vxtbshttpservererrorsthingstocheck)です。

## <a name="cannot_connect"></a>デバッガーがリモート コンピューターに接続できません。

ローカルで、デバッグしている場合、Visual Studio は、32 ビット アプリケーションを 64 ビット バージョンのリモート デバッガーを使用して 64 ビット アプリケーションをデバッグするためにこのエラーが発生する可能性があります。 プロジェクトのプロパティを開き、プロジェクトが正しく、Web サーバーと URL への接続に構成されていることを確認してください。 (開いている**プロパティ > Web > サーバー**または**プロパティ > デバッグ**プロジェクトの種類によって異なります)。

また、HOSTS ファイルを使用している場合は、正しく構成されていることを確認してください。 たとえば、ホストがプロジェクトのプロパティと同様に、同じプロジェクト URL を含める必要がありますをファイル**プロパティ > Web > サーバー**または**プロパティ > デバッグ**プロジェクトの種類に応じて、します。

## <a name="see_help"></a>表示については、一般的な構成エラーです。 デバッガーの外で web ページを実行している可能性があります詳細情報を提供します。

- 実行している Visual Studio と Web サーバー、同じコンピューター上か。 プロジェクトのプロパティを開きを適切な Web サーバーに接続し、URL を起動して、プロジェクトが構成されていることを確認します。 (開いている**プロパティ > Web > サーバー**または**プロパティ > デバッグ**プロジェクトの種類によって異なります)。

- 機能しない、またはリモートでデバッグする、手順に従ってください[IIS 構成を調べて](#vxtbshttpservererrorsthingstocheck)です。

##  <a name="vxtbshttpservererrorsthingstocheck"></a>IIS 構成を確認します。

問題を解決するのにはここで詳細な手順を行った後、デバッグを再試行する前に、IIS をリセットする必要もあります。 管理者特権でコマンド プロンプトを開く」と入力しを実行できます`iisreset`です。 

* 停止し、IIS アプリケーション プールを再起動しますを再試行してください。 

    エラーの結果として、アプリケーション プールを停止した可能性があります。 またはを停止するアプリケーション プールを再起動した別の構成の変更があります。
    
    > [!NOTE]
    > アプリケーション プールを停止して保持する場合、は、コントロール パネルから URL Rewrite モジュールをアンインストールする必要があります。 Web Platform Installer (WebPI) を使用して再インストールすることができます。 この問題は、大量のシステムのアップグレード後に発生する可能性があります。

* アプリケーション プール構成を調べて、修正が必要な場合、再試行してください。

    Visual Studio プロジェクトに一致しない ASP.NET のバージョンについては、アプリケーション プールを構成できます。 アプリケーション プールの ASP.NET バージョンを更新し、それを再起動します。 詳細については、次を参照してください。 [IIS 8.0 を使用して ASP.NET 3.5 と ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)です。

    また、パスワードの資格情報を変更している場合場合があります、アプリケーション プールまたは Web サイトで更新する必要があります。  アプリケーション プール内での資格情報を更新**詳細設定 > プロセス モデル > Identity**です。 Web サイトでの資格情報を更新**基本設定 > として接続しています.**.アプリケーション プールを再起動します。
    
* Web アプリケーションのフォルダーが適切なアクセス許可を持つことを確認してください。

    IIS_IUSRS、iusr アカウント、またはアプリケーション プールの読み取りに関連付けられている特定のユーザーに付与し、Web アプリケーション フォルダーの権限を実行することを確認してください。 問題を修正し、アプリケーション プールを再起動します。

* IIS で ASP.NET の正しいバージョンがインストールされていることを確認します。

    Visual Studio プロジェクトと IIS で ASP.NET のバージョンが一致しないには、この問題が発生します。 Web.config のフレームワークのバージョンを設定する必要があります。IIS で ASP.NET をインストールするには、使用、 [Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)です。 またを参照してください[IIS 8.0 を使用して ASP.NET 3.5 と ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)または ASP.NET Core [IIS と Windows 上のホスト](https://docs.asp.net/en/latest/publishing/iis.html)です。
  
* IP アドレスのみを使用している場合は、認証エラーを解決します

     既定では、IP アドレスはインターネットの一部と見なされ、インターネット上では NTLM 認証が行われません。 Web サイトが認証を要求するように IIS で構成されている場合、この認証は失敗します。 この問題を解決するには、IP アドレスの代わりに、リモート コンピューターの名前を指定できます。
     
## <a name="other-causes"></a>その他の原因

IIS 構成が原因でない、次の手順を試してください。

- 管理者特権で Visual Studio を再起動してからやり直してください。

    Web Deploy を使用するなどの ASP.NET のデバッグ シナリオでは、Visual Studio の高度な特権が必要です。
    
- Visual Studio の複数のインスタンスが実行されている場合 (と管理者特権の場合)、Visual Studio の 1 つのインスタンスでプロジェクトを閉じてもう一度やり直してください。

- ローカル アドレスを持つホスト ファイルを使用している場合は、コンピューターの IP アドレスの代わりに、ループバック アドレスを使用して再試行してください。

    ローカル アドレスを使用していない場合、HOSTS ファイルには、プロジェクトのプロパティと同様に、同じプロジェクト URL が含まれています確認**プロパティ > Web > サーバー**または**プロパティ > デバッグ**に応じて、。プロジェクトの種類。

## <a name="more-troubleshooting-steps"></a>さらにトラブルシューティング手順

* サーバー上のブラウザーで localhost ページを表示します。

     IIS が正しくインストールされていない場合、ブラウザーに `http://localhost` を入力するとエラーが表示されます。
     
     IIS に展開する方法の詳細については、次を参照してください。 [IIS 8.0 を使用して ASP.NET 3.5 と ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)および ASP.NET Core [IIS と Windows 上のホスト](https://docs.asp.net/en/latest/publishing/iis.html)です。

* サーバー上の基本的な ASP.NET アプリケーションの作成 (または、基本的な web.config ファイルを使用)。

    デバッガーを使用するアプリを入手できない場合は、サーバーで、基本的な ASP.NET アプリケーションをローカルに作成してみてください、基本的なアプリをデバッグしようとします。 (既定の ASP.NET MVC テンプレートを使用する可能性があります)。基本的なアプリをデバッグする場合に役立つ 2 つの構成間で異なるかを確認します。 URL 書き換えルールなどは、web.config ファイルで設定の相違を探します。

## <a name="see-also"></a>参照  
 [Web アプリケーションのデバッグ : エラーおよびトラブルシューティング](../debugger/debugging-web-applications-errors-and-troubleshooting.md)