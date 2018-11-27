---
title: 'エラー: Web サーバーでデバッグを開始できません |。Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- FSharp
- VB
- CSharp
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
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 168aaff6e7165c0566b198dab22174b14dad9949
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779295"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>エラー ： Web サーバーでデバッグを開始できません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Web サーバーで実行されている ASP.NET アプリケーションをデバッグしようとする場合、次のエラー メッセージが表示されることがあります。Web サーバーでデバッグを開始できません。
  
多くの場合、IIS が正しく構成されていないためにこのエラーが発生します。

##  <a name="vxtbshttpservererrorsthingstocheck"></a> IIS の構成を確認してください。

詳細なここでは、およびデバッグをもう一度試す前に、問題を解決する手順を実行するには後、は、IIS をリセットする必要がありますも。 管理者のコマンド プロンプトを開き、入力を行うことができます`iisreset`、またはこれを行う IIS マネージャーでします。 

* 停止し、アプリケーション プールを再起動してから、再試行してください。

    アプリケーション プールを停止した可能性があります。 または中止し、アプリケーション プールを再起動することに行った他の構成の変更が必要があります。
    
    > [!NOTE]
    > アプリケーション プールを停止していますが場合、は、コントロール パネルから URL リライト モジュールをアンインストールしてから Web プラットフォーム インストーラー (WPI) を使用して、再インストールする必要があります。 大量のシステムのアップグレード後にこの問題がある可能性があります。

* アプリケーション プール構成を確認、修正が必要な場合、再試行してください。

    パスワードの資格情報が変更されている場合は、アプリケーション プールでそれらを更新する必要があります。 また、ASP.NET を最近インストールした場合、間違ったバージョンの ASP.NET のアプリケーション プールを構成する可能性があります。 問題を修正し、アプリケーション プールを再起動します。
    
* Web アプリケーションのフォルダーが適切なアクセス許可を持つことを確認します。

    IIS_IUSRS に付けることまたは IUSR (またはアプリケーション プールに関連付けられている特定のユーザー) は、読み取りし、実行権限 Web アプリケーション フォルダーの権限を確認します。 問題を修正し、アプリケーション プールを再起動します。

* ローカル アドレスを持つホスト ファイルを使用する場合は、マシンの IP アドレスの代わりに、ループバック アドレスを使用してみてください。

* ブラウザーで localhost ページを表示します。

     IIS が正しくインストールされていない場合、ブラウザーに `http://localhost` を入力するとエラーが表示されます。
     
     IIS への配置方法の詳細については、次を参照してください。 [Remote Debugging ASP.NET on a Remote IIS Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)または ASP.NET Core, [IIS への発行](https://docs.asp.net/en/latest/publishing/iis.html))。

* IIS で ASP.NET の正しいバージョンがインストールされていることを確認します。  参照してください[ASP.NET アプリケーションをデプロイ](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md#BKMK_deploy_asp_net)または ASP.NET Core, [IIS への発行](https://docs.asp.net/en/latest/publishing/iis.html))。

* サーバー上の基本的な ASP.NET アプリケーションを作成します。

     デバッガーを使用するアプリを取得できない場合は、ローカル サーバーで、基本的な ASP.NET アプリケーションを作成してみてくださいし、基本的なアプリをデバッグしようとしてください。 基本的なアプリをデバッグする場合、2 つの構成間で異なるを判断することに役立つ可能性があります。
  
* IP アドレスのみを使用している場合は、認証エラーを解決します

     既定では、IP アドレスはインターネットの一部と見なされ、インターネット上では NTLM 認証が行われません。 認証を要求するように IIS の web サイトを構成する場合は、この認証は失敗します。 この問題を修正するには、IP アドレスではなくリモート コンピューターの名前を指定できます。
     
## <a name="other-causes"></a>その他の原因

: 以前のバージョンの Visual Studio を使用する場合

- 昇格した特権で Visual Studio を再起動してもう一度やり直してください。

    (後ほど修正) 以前のバージョンのバグには、ASP.NET のデバッグ シナリオの一部で管理者特権が必要です。
    
- Visual Studio の複数のインスタンスが実行されている場合、Visual Studio の 1 つのインスタンスでプロジェクトを再び開くもう一度やり直してください。
   
  
## <a name="see-also"></a>関連項目  
 [Web アプリケーションのデバッグ : エラーおよびトラブルシューティング](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



