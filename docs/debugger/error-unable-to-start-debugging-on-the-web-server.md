---
title: エラー :Web サーバーでデバッグを開始できません |。Microsoft Docs
ms.date: 05/23/2017
ms.topic: troubleshooting
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5bf131634dc673fdeefe61fa2238c35fcc2ed8a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938461"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>エラー :Web サーバー上でデバッグを開始できません

Web サーバーで実行されている ASP.NET アプリケーションをデバッグしようとすると、このエラー メッセージが表示可能性があります:`Unable to start debugging on the Web server`します。

多くの場合、アプリケーション プール、IIS をリセット、またはその両方に更新が必要なエラーまたは構成の変更が発生したために、このエラーが発生します。 管理者特権でコマンド プロンプトを開く」と入力して IIS をリセットできます`iisreset`します。 

## <a name="specificerrors"></a>詳細なエラー メッセージとは何ですか。

`Unable to start debugging on the Web server`メッセージは汎用的です。 通常より特定のメッセージがエラーの文字列に含まれより正確な修正プログラムの検索、問題の原因を特定すると役立つ場合があります。 メインのエラー メッセージに追加されるより一般的なエラー メッセージのいくつか次に示します。

- [IIS は、起動に一致する web サイトには示しません url](#IISlist)
- [Web サーバーは正しく構成されていません](#web_server_config)
- [Web サーバーに接続できません。](#unabletoconnect)
- [適切なタイミングで、web サーバーが応答しませんでした。](#webservertimeout)
- [Microsoft Visual Studio リモート デバッグ モニター (msvsmon.exe) は、リモート コンピューター上では実行されていません。](#msvsmon)
- [リモート サーバーがエラーを返しました](#server_error)
- [ASP.NET のデバッグを開始できませんでした。](#aspnet)
- [デバッガーがリモート コンピューターに接続できません。](#cannot_connect)
- [ 一般的な構成エラーについてはヘルプを参照してください。デバッガーの外で web ページを実行している可能性があります詳細情報を提供します。](#see_help)

## <a name="IISlist"></a> IIS は、起動に一致する web サイトには示しません url

- 管理者として Visual Studio を再起動して、デバッグを再試行してください。 (一部 ASP.NET デバッグ シナリオには、高度な特権が必要があります)。

    Visual Studio のショートカット アイコンを右クリックして、常に管理者として実行する Visual Studio を構成することができますを選択する**プロパティ > [詳細設定]**、常に管理者として実行を選択します。

## <a name="web_server_config"></a> Web サーバーは正しく構成されていません

- 参照してください[エラー。](../debugger/error-the-web-server-is-not-configured-correctly.md) Web サーバーは正しく構成されていません

## <a name="unabletoconnect"></a> Web サーバーに接続できません。

- Visual Studio と Web サーバーを同じコンピューターで実行されているを使用したデバッグは**F5** (の代わりに**プロセスにアタッチ**) でしょうか。 プロジェクトのプロパティを開き、適切な Web サーバーに接続し、URL を起動するプロジェクトが構成されていることを確認します。 (開いている**プロパティ > Web > サーバー**または**プロパティ > デバッグ**プロジェクトの種類によって異なります。 Web フォーム プロジェクトを開く**プロパティ ページ > オプションの開始 > サーバー**)。

- それ以外の場合、アプリケーション プールを再起動し、IIS をリセットします。 詳細については、次を参照してください。 [IIS 構成を調べて](#vxtbshttpservererrorsthingstocheck)します。

## <a name="webservertimeout"></a> 適切なタイミングで、web サーバーが応答しませんでした。

- IIS をリセットして、デバッグを再試行してください。 デバッガーの複数のインスタンスは、IIS プロセスにアタッチできます。リセットは終了します。 詳細については、次を参照してください。 [IIS 構成を調べて](#vxtbshttpservererrorsthingstocheck)します。

## <a name="msvsmon"></a> Microsoft Visual Studio リモート デバッグ モニター (msvsmon.exe) は、リモート コンピューター上では実行されていません。

- リモート コンピューターでデバッグする場合は、必ず確保[インストールされ、リモート デバッガーを実行している](../debugger/remote-debugging.md)します。 メッセージは、ファイアウォールをメンション場合、ことを確認、[ファイアウォールでポートを修正](../debugger/remote-debugger-port-assignments.md)サード パーティのファイアウォールを使用している場合は特に、開いています。
- ホスト ファイルを使用している場合は、正しく構成されてを確認します。 たとえばを使用したデバッグ**F5** (の代わりに**プロセスにアタッチ**)、HOSTS ファイル、プロジェクトのプロパティのように同じプロジェクトの URL を含める必要があります**プロパティ > Web > サーバー**または**プロパティ > デバッグ**プロジェクトの種類によって異なります。

## <a name="server_error"></a> リモート サーバーがエラーを返しました

チェック、 [IIS ログ ファイル](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0)エラー サブコードおよび詳細については、この IIS 7[ブログの投稿](https://blogs.iis.net/tomkmvp/troubleshoot-a-403)します。

一般的なエラー コードの一部であり、いくつかの提案をここではさらにです。
- (403) 禁止。 このエラーの考えられる原因の多くがある、そのため、ログ ファイルや web サイトの IIS セキュリティ設定を確認します。 サーバーの web.config が含まれて かどうかを確認`debug=true`compilation 要素にします。 Web アプリケーションのフォルダーが適切な権限を持っていると、アプリケーション プールの構成が (パスワードが変更されている可能性があります) が正しいことを確認してください。 参照してください[IIS 構成を調べて](#vxtbshttpservererrorsthingstocheck)します。 これらの設定は既に修正され、ローカルでデバッグするの場合は、正しいサーバーの種類と URL に接続していることを確認も (で**プロパティ > Web > サーバー**または**プロパティ > デバッグ**、プロジェクトの種類に応じて)。
- (503) サーバーは使用できません。 エラーまたは構成の変更により、アプリケーション プールを停止した可能性があります。 アプリケーション プールを再起動します。
- (404) 見つかりません。 正しいバージョンの ASP.NET のアプリケーション プールが構成されていることを確認します。

## <a name="aspnet"></a> ASP.NET のデバッグを開始できませんでした。

- アプリケーション プールを再起動し、IIS をリセットします。 詳細については、次を参照してください。 [IIS 構成を調べて](#vxtbshttpservererrorsthingstocheck)します。
- URL の書き換えを実行している場合は、プログラムのない URL 書き換えの基本的な web.config をテストします。 参照してください、**注**でモジュールを書き換え URL に関する[の IIS 構成を確認](#vxtbshttpservererrorsthingstocheck)します。

## <a name="cannot_connect"></a> デバッガーがリモート コンピューターに接続できません。

ローカルでデバッグする 64 ビット アプリケーションをデバッグする 64 ビット バージョンのリモート デバッガーを使用して、Visual Studio は 32 ビット アプリケーションであるために、このエラーが発生する可能性があります。 プロジェクトのプロパティを開き、適切な Web サーバーと URL への接続に、プロジェクトが構成されていることを確認します。 (開いている**プロパティ > Web > サーバー**または**プロパティ > デバッグ**プロジェクトの種類によって異なります)。

また、HOSTS ファイルを使用している場合確認が正しく構成されてください。 たとえばの HOSTS ファイル、プロジェクトのプロパティのように同じプロジェクトの URL を含める必要があります**プロパティ > Web > サーバー**または**プロパティ > デバッグ**プロジェクトの種類に応じて。

## <a name="see_help"></a> 一般的な構成エラーについてはヘルプを参照してください。 デバッガーの外で web ページを実行している可能性があります詳細情報を提供します。

- 実行している Visual Studio と Web サーバー、同じコンピューター上ですか。 プロジェクトのプロパティを開き、適切な Web サーバーに接続し、URL を起動するプロジェクトが構成されていることを確認します。 (開いている**プロパティ > Web > サーバー**または**プロパティ > デバッグ**プロジェクトの種類によって異なります)。

- 手順を実行できない、またはリモートでデバッグしている、従います[の IIS 構成を確認](#vxtbshttpservererrorsthingstocheck)します。

##  <a name="vxtbshttpservererrorsthingstocheck"></a> IIS の構成を確認してください。

ここで説明するには、問題を解決する手順を実行した後と、デバッグをもう一度試す前に IIS をリセットする必要もあります。 管理者特権でコマンド プロンプトを開くと、入力して行うことができます`iisreset`します。 

* 停止し、IIS アプリケーション プールを再起動してから、再試行してください。 

    アプリケーション プールは、エラーの結果として停止した可能性があります。 または、中止し、アプリケーション プールを再起動することに行った他の構成の変更が必要があります。
    
    > [!NOTE]
    > アプリケーション プールを停止していますが場合、は、コントロール パネルから、URL Rewrite モジュールをアンインストールする必要があります。 Web Platform Installer (WebPI) を使用して再インストールすることができます。 この問題は、大量のシステムのアップグレード後に発生する可能性があります。

* アプリケーション プール構成を確認、修正が必要な場合、再試行してください。

    Visual Studio プロジェクトに一致しない ASP.NET のバージョンについては、アプリケーション プールを構成できます。 アプリケーション プールで ASP.NET のバージョンを更新し、それを再起動します。 詳細については、次を参照してください。 [IIS 8.0 を使用して ASP.NET 3.5 および ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)します。

    また、パスワードの資格情報が変更されている場合は、アプリケーション プールまたは Web サイトでそれらを更新する必要があります。  アプリケーション プール内での資格情報の更新**詳細設定 > プロセス モデル > Identity**します。 Web サイトの資格情報を更新**基本設定 > として接続しています.**.アプリケーション プールを再起動します。
    
* Web アプリケーションのフォルダーが適切なアクセス許可を持つことを確認します。

    IIS_IUSRS、IUSR を付与するか、特定のユーザーに関連付けられていることを確認、[アプリケーション プール](/iis/manage/configuring-security/application-pool-identities)読み取りし、Web アプリケーション フォルダーの権限を実行します。 問題を修正し、アプリケーション プールを再起動します。

* IIS で ASP.NET の正しいバージョンがインストールされていることを確認します。

    Visual Studio プロジェクトと IIS で ASP.NET のバージョンの不一致には、この問題が発生します。 Web.config で、フレームワークのバージョンを設定する必要があります。IIS で ASP.NET をインストールするには、使用、 [Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)します。 またを参照してください[IIS 8.0 を使用して ASP.NET 3.5 および ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)または ASP.NET Core, [IIS と Windows 上のホスト](https://docs.asp.net/en/latest/publishing/iis.html)します。
  
* IP アドレスのみを使用している場合は、認証エラーを解決します

     既定では、IP アドレスはインターネットの一部と見なされ、インターネット上では NTLM 認証が行われません。 認証を要求するように IIS の web サイトを構成する場合は、この認証が失敗します。 この問題を修正するには、IP アドレスではなくリモート コンピューターの名前を指定できます。
     
## <a name="other-causes"></a>その他の原因

IIS 構成が、問題を引き起こしているしない場合は、次の手順を試してください。

- 管理者特権で Visual Studio を再起動してもう一度やり直してください。

    Web Deploy を使用してなどの一部の ASP.NET デバッグ シナリオでは、Visual Studio の高度な特権が必要です。
    
- Visual Studio の複数のインスタンスが実行されている場合 (管理者特権の場合) を持つ Visual Studio の 1 つのインスタンスでプロジェクトを閉じてもう一度やり直してください。

- ローカル アドレスを持つホスト ファイルを使用する場合は、マシンの IP アドレスの代わりに、ループバック アドレスを使用してみてください。

    ローカル アドレスを使用していない場合、HOSTS ファイルには、プロジェクトのプロパティのように同じプロジェクトの URL が含まれています確認**プロパティ > Web > サーバー**または**プロパティ > デバッグ**に応じて、、。プロジェクトの種類。

## <a name="more-troubleshooting-steps"></a>トラブルシューティングの手順について

* サーバー上のブラウザーで localhost ページを表示します。

     IIS が正しくインストールされていない場合、ブラウザーに `http://localhost` を入力するとエラーが表示されます。
     
     IIS へのデプロイに関する詳細については、次を参照してください。 [IIS 8.0 を使用して ASP.NET 3.5 および ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)と ASP.NET Core, [IIS と Windows 上のホスト](https://docs.asp.net/en/latest/publishing/iis.html)します。

* サーバーの基本的な ASP.NET アプリケーションを作成します (または、基本的な web.config ファイルを使用します。)

    デバッガーを使用するアプリを取得できない場合は、ローカル サーバーで、基本的な ASP.NET アプリケーションを作成してみてくださいし、基本的なアプリをデバッグしようとしてください。 (既定の ASP.NET MVC テンプレートを使用する可能性があります)。基本的なアプリをデバッグする場合、2 つの構成間で異なるを判断することに役立つ可能性があります。 URL 書き換えルールなどは、web.config ファイルで設定の相違を探します。

## <a name="see-also"></a>関連項目
 [Web アプリケーションのデバッグ: エラーとトラブルシューティング](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
