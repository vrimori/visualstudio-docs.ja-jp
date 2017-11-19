---
title: "サーバーとクライアント構成の問題 ClickOnce 配置 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- Windows applications, ClickOnce deployments
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
caps.latest.revision: "33"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 4b7153b0a20c10e7dbdb31ac943f150f72cb39d8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>ClickOnce 配置でのサーバーおよびクライアント構成の問題
Windows server インターネット インフォメーション サービス (IIS) を使用する、展開には、Windows で認識されないファイルの種類が含まれている場合は、Microsoft Word ファイルなど、そのファイルを送信する IIS は拒否し、配置は失敗します。  
  
 さらに、いくつかの Web サーバーと、アプリケーション ソフトウェアをなど、Web[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]ファイルの一覧を含む、およびファイルの種類をダウンロードすることはできません。 たとえば、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]すべて Web.config ファイルのダウンロードを防ぎます。 これらのファイルには、ユーザー名とパスワードなどの機密情報を含めることがあります。  
  
 この制限は特に問題は発生コアをダウンロードするためが[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]マニフェスト、アセンブリなどのファイル、この制限できないことがありますの一部として含まれるデータ ファイルをダウンロード、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションです。 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]、IIS 構成マネージャーからこのようなファイルのダウンロードを禁止するハンドラーを削除することでこのエラーを解決することができます。 追加の詳細については、IIS サーバーのマニュアルを参照してください。  
  
 一部の Web サーバーは、.dll、.config、.mdf ファイルなどの拡張子を持つファイルをブロック可能性があります。 通常、Windows ベースのアプリケーションには、これらの拡張機能の一部を持つファイルが含まれます。 ユーザーが実行を試みると、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Web サーバーでブロックされているファイルにアクセスするアプリケーションでは、エラーが発生します。 すべてのファイル拡張子のブロックを解除するのではなく[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]既定では".deploy"ファイル拡張子を持つすべてのアプリケーション ファイルを発行します。 したがって、管理者は、次の 3 つのファイル拡張子のブロックを解除する Web サーバーを構成するだけが必要。  
  
-   .application  
  
-   .manifest  
  
-   .deploy  
  
 ただし、このオプションを無効にオフにすることができます、 **".deploy"ファイル拡張子を使用して** オプションを選択、[発行オプション ダイアログ ボックス](http://msdn.microsoft.com/en-us/fd9baa1b-7311-4f9e-8ffb-ae50cf110592)、いる場合、すべてのファイル拡張子のブロックを解除する Web サーバーを構成する必要がありますアプリケーションで使用されます。  
  
 IIS をインストールしていないを使用している場合に .manifest が付いたもの、.application、および .deploy、たとえば、構成する必要が、 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]、または別の Web サーバー (たとえば、Apache) を使用している場合。  
  
## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce と Secure Sockets Layer (SSL)  
 A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション SSL 上で Internet Explorer が SSL 証明書に関するメッセージを生成するとき以外は問題なく動作します。 プロンプトは、有効期限が切れたときにサイト名が一致しないなど、証明書または証明書に何らかの問題がある場合に生成されることができます。 させる[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]SSL 接続経由での作業、証明書が、最新の状態であり、証明書のデータがサイト データを照合することを確認してください。  
  
## <a name="clickonce-and-proxy-authentication"></a>ClickOnce とプロキシの認証  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].NET Framework 3.5 以降で Windows 統合のプロキシ認証のサポートを提供します。 特定の machine.config ディレクティブは必要ありません。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]基本認証またはダイジェストなどの他の認証プロトコルのサポートを行いません。  
  
 この機能を有効にする .NET Framework 2.0 に修正プログラムを適用することもできます。 詳細については、http://go.microsoft.com/fwlink/?LinkId=158730 を参照してください。  
  
 詳細については、次を参照してください。 [ \<defaultProxy > 要素 (ネットワーク設定)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings)です。  
  
## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce と Web ブラウザーの互換性  
 現在、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]配置マニフェストへの URL が Internet Explorer で開かれている場合にのみのインストールが起動します。 Internet Explorer が既定の Web ブラウザーとして設定されている場合にのみ、Microsoft Office Outlook などの別のアプリケーションが起動される URL の展開が正常に起動されます。  
  
> [!NOTE]
>  Mozilla Firefox には、配置プロバイダが空白でないか、Microsoft .NET Framework アシスタントの拡張機能がインストールされている場合はサポートされています。 この拡張機能は、.NET Framework 3.5 SP1 に同梱されています。 XBAP サポートについては、必要なときに、プラグイン NPWPF にアクティブ化されます。  
  
## <a name="activating-clickonce-applications-through-browser-scripting"></a>ブラウザーがスクリプトを通じて ClickOnce アプリケーションをアクティブ化  
 起動するカスタム Web ページを開発しているかどうか、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アクティブ スクリプティングを使用してアプリケーションを一部のコンピューターでアプリケーションが起動しないことがあります。 Internet Explorer には、という設定が含まれています。**ファイルのダウンロードに自動確認**、この動作に影響します。 この設定は、**セキュリティ** タブでその**オプション** メニューのこの動作に影響します。 呼び出された**ファイルのダウンロードに自動確認**の下に記載されていると、**ダウンロード**カテゴリ。 プロパティに設定**を有効にする**既定ではイントラネットの Web ページと**を無効にする**既定では、インターネットの Web ページ。 この設定を設定すると**を無効にする**をアクティブ化しようとすると、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション プログラム (などによって、その URL への割り当て、`document.location`プロパティ) はブロックされます。 このような状況は、ユーザーを起動できますのみ、ユーザーが開始したダウンロード経由でのアプリケーションなど、アプリケーションの URL に設定されたハイパーリンクをクリックしています。  
  
## <a name="additional-server-configuration-issues"></a>その他のサーバーの構成の問題  
  
##### <a name="administrator-permissions-required"></a>必要な管理者権限  
 HTTP で公開している場合は、対象サーバーで管理者のアクセス許可が必要です。 IIS では、このアクセス許可レベルが必要です。 発行されるわけで HTTP を使用して場合、する必要があります書き込みアクセス権だけターゲット パス。  
  
##### <a name="server-authentication-issues"></a>サーバー認証の問題  
 "匿名アクセス権を持つ"をオフになっているリモート サーバーにパブリッシュするときに、次の警告が表示されます。  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
>  NTLM (NT チャレンジ/レスポンス) 認証サイトが既定の資格情報以外の資格情報の入力が求め、セキュリティ ダイアログ ボックスをクリックすると作業を行うことができます**OK**求められた場合、指定された保存する場合今後のセッションの資格情報。 ただし、この回避策は、基本認証は動作しません。  
  
## <a name="using-third-party-web-servers"></a>サード パーティの Web サーバーを使用します。  
 展開する場合は、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] IIS 以外の Web サーバーからアプリケーションを可能性があります問題が発生する場合は、サーバーがキーの無効なコンテンツ型を返す[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]など、配置マニフェストとアプリケーション マニフェストのファイルです。 この問題を解決するのには、Web サーバーのヘルプが設定されているサーバーに新しいコンテンツ タイプを追加し、ファイル名拡張子のすべてのマッピングを次の表に表示されていることを確認する方法に関するドキュメントを参照してください。  
  
|ファイル名拡張子|コンテンツの種類|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## <a name="clickonce-and-mapped-drives"></a>ClickOnce とマップされたドライブ  
 Visual Studio を使用して ClickOnce アプリケーションを発行する場合は、インストール場所として、マップされたドライブを指定できません。 ただし、Manifest Generator およびエディター (Mage.exe および MageUI.exe) を使用して、マップされたドライブからインストールする ClickOnce アプリケーションを変更することができます。 詳細については、次を参照してください。 [Mage.exe (マニフェスト生成および編集ツール)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)と[MageUI.exe (マニフェスト生成および編集ツールのグラフィカル クライアント)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)です。  
  
## <a name="ftp-protocol-not-supported-for-installing-applications"></a>FTP プロトコルがアプリケーションをインストールするためにサポートされていません  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]任意の HTTP 1.1 Web サーバーまたはファイル サーバーからアプリケーションのインストールをサポートします。 アプリケーションをインストールするのには、FTP、ファイル転送プロトコルはサポートされていません。 FTP を使用して、アプリケーションのみを公開することができます。 次の表には、これらの相違点をまとめたものです。  
  
|URL の種類|説明|  
|--------------|-----------------|  
|ftp://|発行することができます、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]このプロトコルを使用してアプリケーションです。|  
|http://|インストールすることができます、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]このプロトコルを使用してアプリケーションです。|  
|https://|インストールすることができます、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]このプロトコルを使用してアプリケーションです。|  
|file://|インストールすることができます、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]このプロトコルを使用してアプリケーションです。|  
  
## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: Windows ファイアウォール  
 既定では、Windows XP SP2、Windows ファイアウォールを有効にします。 Windows XP がインストールされているコンピューター上のアプリケーションを開発している場合は、引き続き発行および実行[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]IIS を実行しているローカル サーバーからのアプリケーションです。 ただし、Windows ファイアウォールを開く場合を除いて他のコンピューターから IIS を実行するサーバーにアクセスできません。 Windows ファイアウォールを管理する手順については、Windows のヘルプを参照してください。  
  
## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server:、FrontPage server extensions が有効にします。  
 Microsoft の FrontPage Server Extensions は、HTTP を使用する Windows の Web サーバーにアプリケーションの発行に必要です。  
  
 既定では、Windows Server にインストールされている FrontPage Server Extensions はありません。 使用する場合[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]FrontPage Server Extensions で HTTP を使用する Windows Server の Web サーバーで発行する必要があります最初にインストールする FrontPage Server Extensions です。 Windows Server では、管理サーバーの管理ツールを使用してインストールを実行することができます。  
  
## <a name="windows-server-locked-down-content-types"></a>Windows Server: ロックされたコンテンツの種類  
 上の IIS[!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)]特定既知のコンテンツ タイプ (たとえば、.htm、.html、.txt、およびなど) を除くすべてのファイルの種類がロックされます。 展開を有効にする[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションがこのサーバーを使用して、型 .application、マニフェスト、およびアプリケーションで使用されるその他のカスタムのファイルの種類のファイルをダウンロードできるように IIS 設定を変更する必要があります。  
  
 IIS サーバーを使用して、展開する場合は、inetmgr.exe を実行し、既定の Web ページの新しいファイルの種類を追加します。  
  
-   .Application と .manifest 拡張機能の場合は、MIME の種類が「/x ms-アプリケーションです」をする必要があります。 その他のファイルの種類の MIME の種類が「アプリケーション/オクテット ストリームです」をする必要があります。  
  
-   拡張子の MIME の種類を作成する場合は"*"と MIME の種類「アプリケーション/オクテット ストリーム」では、ファイルのダウンロードをブロックされていないファイルの種類が許可されます。 (ただし、ブロック ファイル .aspx、.asmx などの種類をダウンロードすることはできません)。  
  
 Microsoft サポート技術情報の記事 KB326965、「IIS 6.0 はない機能不明な MIME の種類」を参照して Windows Server で MIME の種類の構成に関する特定の手順については、 [http://support.microsoft.com/default.aspx?scid=kb;en-us;326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965).  
  
## <a name="content-type-mappings"></a>コンテンツの種類のマッピング  
 HTTP 経由で公開するとき、.application ファイルのコンテンツ タイプ (MIME の種類とも呼ばれます) は「/x ms-アプリケーションです」をする必要があります。 使用していれば[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]をサーバーにインストールが設定されます。 を自動的にします。 これがインストールされていないかどうかは、MIME の種類の関連付けを作成する必要があります、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション vroot (またはサーバー全体)。  
  
 IIS サーバーを使用して、展開する場合は、inetmgr.exe を実行し、「/x ms-アプリケーション」は .application という拡張子の新しいコンテンツ タイプを追加します。  
  
## <a name="http-compression-issues"></a>HTTP の圧縮の問題  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]、HTTP 圧縮を使用したダウンロード、クライアントにストリームを送信する前に、データ ストリームを圧縮に GZIP アルゴリズムを使用する Web サーバー テクノロジを行うことができます。 クライアント: この場合、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]: ファイルを読み取る前に、ストリームの圧縮を解除します。  
  
 IIS を使用している場合は、HTTP 圧縮を簡単に有効にできます。 ただし、HTTP 圧縮を有効にするはでのみ有効な種類のファイル、つまり、HTML やテキスト ファイルです。 アセンブリ (.dll) の圧縮を有効にするには、XML (.xml)、配置マニフェスト (.application)、およびアプリケーション マニフェスト (マニフェスト) する必要があります追加するファイルの種類を圧縮する IIS の種類の一覧にします。 ファイルの種類を展開に追加するまで、テキストと HTML ファイルのみが圧縮されます。  
  
 IIS の詳細な手順については、次を参照してください。 [HTTP 圧縮対象のドキュメントの種類を指定する方法](http://go.microsoft.com/fwlink/?LinkId=178459)です。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce 配置のトラブルシューティング](../deployment/troubleshooting-clickonce-deployments.md)   
 [ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [アプリケーション配置の必要条件](../deployment/application-deployment-prerequisites.md)