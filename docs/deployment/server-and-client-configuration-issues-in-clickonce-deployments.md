---
title: サーバーと ClickOnce 配置でのクライアント構成の問題 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 56b9e68767d4191aab016e3c0d976efb808aff01
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44282613"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>ClickOnce 配置でサーバーとクライアントの構成に関する問題
Windows Server で、インターネット インフォメーション サービス (IIS) を使用する、展開には、Windows で認識されない種類のファイルが含まれている場合は、Microsoft Word ファイルなど、そのファイルを送信する IIS は拒否し、配置は失敗します。  
  
 さらに、いくつかの Web サーバーと、アプリケーション ソフトウェアなどの Web[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]ファイルの一覧を含み、ファイルの種類をダウンロードすることはできません。 たとえば、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]すべてがダウンロードされなくなり*Web.config*ファイル。 これらのファイルには、ユーザー名とパスワードなどの機密情報を含めることができます。  
  
 Core のダウンロードの問題を原因がする必要がありますこの制限がない[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]ファイル マニフェスト、アセンブリなど、この制限できない可能性がの一部として含まれているデータ ファイルをダウンロードしてから、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション。 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]IIS の configuration manager からこのようなファイルのダウンロードを禁止するハンドラーを削除することによってこのエラーを解決することができます。 詳細については、IIS server のドキュメントを参照してください。  
  
 一部の Web サーバーなどの拡張子を持つファイルを妨げる *.dll*、 *.config*、および *.mdf*します。 通常、Windows ベースのアプリケーションには、これらの拡張機能の一部のファイルが含まれます。 ユーザーが実行する場合、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Web サーバーでブロックされているファイルにアクセスするアプリケーションでは、エラーが発生します。 すべてのファイル拡張子のブロックを解除するのではなく[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]すべてのアプリケーション ファイルの発行、 *.deploy*既定ではファイル拡張子。 そのため、管理者では、次の 3 つのファイル拡張子のブロックを解除する Web サーバーを構成する必要がのみ。  
  
-   *.application*  
  
-   *.manifest*  
  
-   *.deploy* 
  
 オフにすると、このオプションを無効にするただし、 **".deploy"ファイル拡張子を使用して、** オプションを[Publish Options Dialog Box](/previous-versions/visualstudio/visual-studio-2010/7z83t16a(v=vs.100))、その場合、すべてのファイル拡張子のブロックを解除する Web サーバーを構成する必要がありますアプリケーションで使用されます。  
  
 構成する必要があります *.manifest*、 *.application*、および *.deploy*、たとえば、IIS をインストールしていないを使用しているかどうか、 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]、または場合別の Web サーバー (Apache など) を使用します。  
  
## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce と Secure Sockets Layer (SSL)  
 A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション、SSL 経由で Internet Explorer で SSL 証明書に関するプロンプトを生成するとき以外は問題なく動作します。 プロンプトは、有効期限が切れたときに、サイト名が一致しないなど、証明書または証明書に何らかの問題がある場合に発生することができます。 させる[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]SSL 接続経由で動作、証明書が、最新の状態であり、証明書のデータがサイト データと一致するかどうかを確認します。  
  
## <a name="clickonce-and-proxy-authentication"></a>ClickOnce とプロキシの認証  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .NET Framework 3.5 以降で Windows 統合のプロキシ認証のサポートを提供します。 特定の machine.config ディレクティブは必要ありません。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 基本認証またはダイジェストなどの他の認証プロトコルのサポートを行いません。  
  
 この機能を有効にする .NET Framework 2.0 修正プログラムを適用することもできます。 詳細については、「 http://go.microsoft.com/fwlink/?LinkId=158730」を参照してください。  
  
 詳細については、次を参照してください。 [ \<defaultProxy > 要素 (ネットワーク設定)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings)します。  
  
## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce と Web ブラウザーの互換性  
 現時点では、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]配置マニフェストへの URL が Internet Explorer で開かれている場合にのみインストールが起動します。 Internet Explorer が既定の Web ブラウザーとして設定されている場合にのみ、Microsoft Office Outlook などの別のアプリケーションが起動される URL のデプロイが正常に起動します。  
  
> [!NOTE]
>  Mozilla Firefox は、配置プロバイダーが空白でないか、Microsoft .NET Framework Assistant の拡張機能がインストールされている場合にサポートされます。 この拡張機能は、.NET Framework 3.5 SP1 と共にパッケージ化されます。 XBAP サポートについては、必要なときに、プラグインの NPWPF がアクティブになります。  
  
## <a name="activate-clickonce-applications-through-browser-scripting"></a>ブラウザーのスクリプトを通じて ClickOnce アプリケーションをアクティブ化します。  
 開発したカスタムの Web ページを起動するかどうか、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アクティブ スクリプトを使用してアプリケーション、アプリケーションがいくつかのマシンの起動はしないことがわかります。 Internet Explorer にはと呼ばれる設定が含まれています**自動的な確認ダイアログ ファイルのダウンロード**、この動作に影響します。 この設定は、**セキュリティ** タブでその**オプション** メニューのこの動作に影響します。 呼び出された**自動的な確認ダイアログ ファイルのダウンロード**、下に記載されていると、**ダウンロード**カテゴリ。 設定されて**を有効にする**イントラネット Web ページに既定で**を無効にする**Internet の Web ページの既定でします。 この設定を設定すると**を無効にする**とアクティブ化すると、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション プログラムで (すると、URL を割り当てることで、たとえば、`document.location`プロパティ) はブロックされます。 このような状況では、ユーザー アプリケーションを起動できます、ユーザーが開始したダウンロードのみをたとえば、アプリケーションの URL に設定されたハイパーリンクをクリックしています。  
  
## <a name="additional-server-configuration-issues"></a>追加のサーバー構成の問題  
  
##### <a name="administrator-permissions-required"></a>管理者権限が必要  
 HTTP で発行している場合は、対象サーバーで管理者のアクセス許可があります。 IIS では、このアクセス許可レベルが必要です。 HTTP を使用して、発行しない場合のみ必要があります記述するためのアクセス許可ターゲット パス。  
  
##### <a name="server-authentication-issues"></a>サーバー認証の問題  
 匿名アクセス"は無効にされているリモート サーバーに公開するとき、次の警告が表示されます。  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
>  NTLM (NT チャレンジ/レスポンス) 認証を求めるメッセージが既定の資格情報以外の資格情報のセキュリティ ダイアログ ボックスで、クリックして、機能を行うことができます**OK**を求められた場合は、指定された保存します。今後のセッションの資格情報。 ただし、この回避策は、基本認証は機能しません。  
  
## <a name="use-third-party-web-servers"></a>サード パーティの Web サーバーを使用します。  
 展開する場合、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] IIS 以外の Web サーバーからアプリケーションが問題が発生したサーバーがキーの不適切なコンテンツの種類を返す場合[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]など、配置マニフェストとアプリケーション マニフェスト ファイル。 この問題を解決するには、Web サーバーのヘルプが設定されているサーバーに新しいコンテンツ タイプを追加し、すべてのファイル名拡張子マッピングを次の表に表示されていることを確認する方法に関するドキュメントを参照してください。  
  
|ファイル名拡張子|コンテンツの種類|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## <a name="clickonce-and-mapped-drives"></a>ClickOnce とマップされたドライブ  
 Visual Studio を使用して ClickOnce アプリケーションを発行する場合は、インストール場所として、マップされたドライブを指定できません。 ただし、マニフェスト ジェネレーターおよびエディター (Mage.exe および MageUI.exe) を使用してマップされたドライブからインストールする ClickOnce アプリケーションを変更できます。 詳細については、次を参照してください。 [Mage.exe (マニフェスト生成および編集ツール)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)と[MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)します。  
  
## <a name="ftp-protocol-not-supported-for-installing-applications"></a>FTP プロトコルのアプリケーションをインストールするためにサポートされていません  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] HTTP 1.1 の Web サーバーまたはファイル サーバーからアプリケーションのインストールをサポートします。 アプリケーションをインストールするのには、FTP、ファイル転送プロトコルはサポートされていません。 アプリケーションのみを公開するのに FTP を使用することができます。 次の表は、これらの違いをまとめたものです。  
  
|URL の種類|説明|  
|--------------|-----------------|  
|ftp://|発行することができます、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]このプロトコルを使用してアプリケーション。|  
|http://|インストールすることができます、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]このプロトコルを使用してアプリケーション。|  
|https://|インストールすることができます、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]このプロトコルを使用してアプリケーション。|  
|file://|インストールすることができます、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]このプロトコルを使用してアプリケーション。|  
  
## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP sp 2: Windows ファイアウォール  
 既定では、Windows XP SP2、Windows ファイアウォールが可能です。 発行および実行する場合は Windows XP がインストールされているコンピューター上でアプリケーションを開発している場合[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]IIS を実行しているローカル サーバーからのアプリケーション。 ただし、Windows ファイアウォールを開く場合を除き、別のコンピューターから IIS を実行するサーバーはアクセスできません。 Windows ファイアウォールを管理する手順については、Windows のヘルプを参照してください。  
  
## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server:、FrontPage server extensions が有効にします。  
 Microsoft の FrontPage Server Extensions は、HTTP を使用する Windows の Web サーバーにアプリケーションの発行に必要です。  
  
 既定では、Windows Server にインストールされている FrontPage Server Extensions はありません。 使用する場合[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]FrontPage Server Extensions で HTTP を使用する Windows Server の Web サーバーで発行する必要があります最初にインストールする FrontPage Server Extensions。 インストールを実行するには、Windows Server のサーバーの管理の管理ツールを使用します。  
  
## <a name="windows-server-locked-down-content-types"></a>Windows Server: ロックされたコンテンツの種類  
 上の IIS[!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)]ロックは特定の既知のコンテンツ タイプを除くすべてのファイルの種類 (たとえば、 *.htm*、 *.html*、 *.txt*など)。 展開を有効にする[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]の種類のファイルをダウンロードできるようにするのには、IIS 設定を変更する必要があるアプリケーションがこのサーバーを使用して、 *.application*、 *.manifest*、およびその他のカスタムのファイルの種類アプリケーションで使用します。  
  
 IIS サーバーを使用してを展開する場合は、実行*inetmgr.exe*し、既定の Web ページの新しいファイルの種類を追加します。  
  
-   *.Application*と *.manifest*拡張機能では、MIME の種類は「/x ms-アプリケーションです」をする必要があります。 その他のファイルの種類の MIME の種類が「アプリケーションまたはオクテット ストリームです」をする必要があります。  
  
-   拡張子の MIME の種類を作成する場合は、"*"MIME の種類「アプリケーションまたはオクテット ストリーム」では、そのファイルのダウンロードをブロックされていないファイルの種類が許可されます。 (ただし、ファイルの種類をなどブロック *.aspx*と *.asmx*ダウンロードすることはできません)。  
  
 Windows Server の MIME の種類を構成する方法については、マイクロソフト サポート技術情報記事 KB326965 を参照してください、「IIS 6.0 は処理しません不明な MIME の種類」で[ http://support.microsoft.com/default.aspx?scid=kb; en-私たち; 326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965)します。  
  
## <a name="content-type-mappings"></a>コンテンツの種類のマッピング  
 コンテンツの種類 (MIME の種類とも呼ばれます)、HTTP 経由で発行するときに、 *.application*ファイルが「/x ms-アプリケーションです」にする必要があります。 あれば[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]サーバーにインストール、設定されます。 が自動的にします。 これがインストールされていないかどうかは、MIME の種類の関連付けを作成する必要がある、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション vroot (またはサーバー全体)。  
  
 IIS サーバーを使用してを展開する場合は、実行*inetmgr* 。exe の「application/x-ms-アプリケーション」の新しいコンテンツの種類を追加し、 *.application*拡張機能。  
  
## <a name="http-compression-issues"></a>HTTP 圧縮の問題  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]、HTTP 圧縮を使用するダウンロード、クライアントにストリームを送信する前にデータ ストリームを圧縮する、GZIP アルゴリズムを使用する Web サーバー テクノロジを行うことができます。 クライアント: この場合、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-ファイルを読み取る前に、ストリームの圧縮を解除します。  
  
 IIS を使用している場合、HTTP 圧縮を簡単に実現できます。 ただし、HTTP 圧縮を有効にした場合にのみなっての特定のファイルの種類、つまり、HTML やテキスト ファイル。 アセンブリの圧縮を有効にする (*.dll*)、XML (*.xml*)、配置マニフェスト (*.application*)、およびアプリケーション マニフェスト (*.manifest*)、これらのファイルを圧縮する IIS の種類の一覧に種類を追加する必要があります。 配置にファイルの種類を追加するまで、テキストや HTML ファイルのみが圧縮されます。  
  
 IIS の詳細な手順については、次を参照してください。 [HTTP 圧縮のドキュメントの種類を指定する方法](http://go.microsoft.com/fwlink/?LinkId=178459)します。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce 配置をトラブルシューティングします。](../deployment/troubleshooting-clickonce-deployments.md)   
 [ClickOnce 配置ストラテジを選択します。](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [アプリケーション配置の必要条件](../deployment/application-deployment-prerequisites.md)