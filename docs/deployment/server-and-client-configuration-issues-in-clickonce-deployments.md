---
title: "ClickOnce 配置でのサーバーおよびクライアント構成の問題 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 配置, トラブルシューティング"
  - "配置 (アプリケーションを), ClickOnce"
  - "トラブルシューティング (ClickOnce 配置を)"
  - "Windows アプリケーション, ClickOnce 配置"
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
caps.latest.revision: 33
caps.handback.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce 配置でのサーバーおよびクライアント構成の問題
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Windows Server でインターネット インフォメーション サービス \(IIS\) を使用しており、Microsoft Word ファイルなど Windows で確認できない種類のファイルが配置に含まれている場合には、IIS によってこのファイルの転送が拒否されるため、配置が失敗します。  
  
 また、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] などの Web サーバーや Web アプリケーション ソフトウェアの一部では、ダウンロードできないファイルやファイルの種類が一覧で指定されています。  たとえば、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] では、Web.config ファイルを一切ダウンロードできません。  これらのファイルには、ユーザー名やパスワードなどの重要情報が含まれている場合があります。  
  
 これによって、マニフェスト、アセンブリなど [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] の主要なファイルのダウンロードが制限されることはありませんが、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションの一部として含まれているデータ ファイルをダウンロードできなくなる可能性があります。  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] では、このようなファイルのダウンロードを妨げるハンドラーを IIS 構成マネージャーから削除することによって、このエラーを解決できます。  詳細については、IIS サーバーのドキュメントを参照してください。  
  
 Web サーバーによっては、.dll、.config、.mdf などの拡張子を持つファイルをブロックする場合があります。  通常、Windows ベースのアプリケーションには、これらの拡張子のいずれかを持つファイルが含まれています。  Web サーバー上のブロックされたファイルにアクセスする [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションをユーザーが実行しようとすると、エラーが発生します。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] では、すべてのファイル拡張子のブロックを解除しなくても、すべてのアプリケーション ファイルが ".deploy" ファイル拡張子で発行されるように既定で設定されています。  このため、管理者は次の 3 つのファイル拡張子のブロックを解除するように Web サーバーを構成するだけで済みます。  
  
-   .application  
  
-   .manifest  
  
-   .deploy  
  
 ただし、アプリケーションで使用されているすべてのファイル拡張子のブロックを解除するように Web サーバーを構成する必要がある場合は、[Publish Options Dialog Box](http://msdn.microsoft.com/ja-jp/fd9baa1b-7311-4f9e-8ffb-ae50cf110592)の **\[".deploy" ファイル拡張子を使用する\]** をオフにします。  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] がインストールされていない IIS を使用している場合や、別の Web サーバー \(Apache など\) を使用している場合などには、.manifest、.application、および .deploy を設定する必要があります。  
  
## ClickOnce と Secure Sockets Layer \(SSL\)  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションは SSL 経由でも適切に動作します。ただし、Internet Explorer で SSL 証明書についてのプロンプトが表示された場合は別です。  このプロンプトは、証明書に何らかの問題がある場合 \(たとえば、サイト名が一致しない場合や、証明書の有効期限が切れている場合など\) に表示されます。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] を SSL 接続経由で適切に動作させるためには、証明書が最新であることと、証明書のデータがサイトのデータに一致することを確認してください。  
  
## ClickOnce とプロキシ認証  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] は、.NET Framework 3.5 から Windows 統合プロキシ認証をサポートしています。  特定の machine.config ディレクティブは必要ありません。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] は、基本認証やダイジェスト認証などのその他の認証プロトコルはサポートしません。  
  
 また、.NET Framework 2.0 の修正プログラムを適用して、この機能を有効にすることもできます。  詳細については、http:\/\/go.microsoft.com\/fwlink\/?LinkId\=158730 を参照してください。  
  
 詳細については、「[\<defaultProxy\> 要素 \(ネットワーク設定\)](../Topic/%3CdefaultProxy%3E%20Element%20\(Network%20Settings\).md)」を参照してください。  
  
## ClickOnce と Web ブラウザーの互換性  
 現在、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] のインストールは、配置マニフェストへの URL が Internet Explorer で開かれている場合にのみ起動できます。  配置の URL が Microsoft Office Outlook などの別のアプリケーションから起動されているときは、Internet Explorer が既定の Web ブラウザーとして設定されている場合にのみ配置が正常に起動されます。  
  
> [!NOTE]
>  Mozilla Firefox がサポートされるのは、配置プロバイダーが空白でないか、Microsoft .NET Framework Assistant 拡張機能がインストールされている場合です。  この拡張機能は、.NET Framework 3.5 SP1 に含まれています。  XBAP をサポートするため、NPWPF プラグインが必要に応じてアクティブ化されます。  
  
## ブラウザー スクリプトによる ClickOnce アプリケーションのアクティブ化  
 アクティブ スクリプトを使用して [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを起動するカスタム Web ページを開発した場合、一部のコンピューターでアプリケーションが起動されないことがあります。  Internet Explorer には **\[ファイルのダウンロード時に自動的にダイアログを表示\]** という設定があり、これがこの動作に影響します。  この設定は、この動作に影響を与える **\[インターネット オプション\]** の **\[セキュリティ\]** タブで行うことができます。  これは **\[ファイルのダウンロード時に自動的にダイアログを表示\]** という設定で、**\[ダウンロード\]** カテゴリの下に表示されます。  このプロパティは、イントラネット Web ページに対しては既定で **\[有効にする\]**  に設定されており、インターネット Web ページに対しては既定で **\[無効にする\]** に設定されています。  この設定を **\[無効にする\]** に設定すると、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションをプログラムでアクティブ化する試み \(たとえば、その URL を `document.location` プロパティに割り当てるなどの試み\) がすべてブロックされます。  このような状況でユーザーがアプリケーションを起動するには、アプリケーションの URL に設定されたハイパーリンクをクリックするなどして、ユーザーがダウンロードを実行するしかありません。  
  
## サーバー構成に関するその他の問題  
  
##### 管理者のアクセス許可が必要  
 HTTP を使用して発行する場合は、対象のサーバーで管理者のアクセス許可を持っていることが必要です。  IIS でこのアクセス許可レベルが必要となります。  HTTP を使用する発行を行わない場合には、対象のパスへの書き込みアクセス許可だけが必要となります。  
  
##### サーバー認証の問題  
 \[匿名アクセス\] をオフにしてリモート サーバーへの発行を行うと、次の警告が表示されます。  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
>  既定の資格情報と異なる資格情報の指定をサイトから要求され、セキュリティ ダイアログ ボックスで、指定した資格情報を今後のセッション用に保存するかどうかを確認するメッセージが表示されたときに **\[OK\]** をクリックした場合には、NTLM \(NT チャレンジ応答\) 認証を機能させることができます。  ただし、この回避策は基本認証では使うことができません。  
  
## サードパーティの Web サーバーの使用  
 IIS 以外の Web サーバーから [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを配置する場合、配置マニフェスト、アプリケーション マニフェストなどの主要な [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ファイルに対してサーバーが不正なコンテンツ タイプを返すと問題が発生する場合があります。  この問題を解決するには、新しいコンテンツ タイプをサーバーに追加する方法に関する Web サーバーのヘルプ ドキュメントを参照し、次の表に記載されているすべてのファイル名の拡張子が正しく割り当てられていることを確認します。  
  
|ファイル名の拡張子|コンテンツ タイプ|  
|---------------|---------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## ClickOnce と割り当てられたドライブ  
 Visual Studio を使用して ClickOnce アプリケーションを発行する場合、インストール場所として割り当てられたドライブを指定することはできません。  ただし、マニフェスト ジェネレーターおよびエディター \(Mage.exe および MageUI.exe\) を使用して、マップされたドライブからインストールできるように ClickOnce アプリケーションを変更できます。  詳細については、「[Mage.exe \(マニフェストの生成および編集ツール\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)」および「[MageUI.exe \(マニフェスト生成および編集ツールのグラフィカル クライアント\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)」を参照してください。  
  
## アプリケーションのインストールをサポートしない FTP プロトコル  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] は、HTTP 1.1 のあらゆる Web サーバーとファイル サーバーからのアプリケーションのインストールをサポートしています。  ファイル転送プロトコル \(FTP: File Transfer Protocol\) はアプリケーションのインストールをサポートしていません。  FTP は、アプリケーションの発行にのみ使用できます。  これらの相違点の概要を次の表に示します。  
  
|URL タイプ|Description|  
|-------------|-----------------|  
|ftp:\/\/|このプロトコルを使用すると、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを発行できます。|  
|http:\/\/|このプロトコルを使用すると、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションをインストールできます。|  
|https:\/\/|このプロトコルを使用すると、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションをインストールできます。|  
|file:\/\/|このプロトコルを使用すると、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションをインストールできます。|  
  
## Windows XP SP2: Windows ファイアウォール  
 Windows XP SP2 の既定では、Windows ファイアウォールが有効になっています。  Windows XP がインストールされているコンピューターでアプリケーションを開発している場合でも、IIS を実行中のローカル サーバーから [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを発行および実行できます。  しかし、IIS を実行中のそのサーバーに他のコンピューターからアクセスする場合は、Windows ファイアウォールを開かないとアクセスできません。  Windows ファイアウォールを管理する手順については、Windows ヘルプを参照してください。  
  
## Windows Server : FrontPage Server Extensions の有効化  
 HTTP を使用する Windows Web サーバーにアプリケーションを発行するには、Microsoft が提供する FrontPage Server Extensions が必要です。  
  
 既定では、Windows Server には FrontPage Server Extensions はインストールされていません。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を使用して、HTTP を使用する Windows Server の Web サーバーに対して FrontPage Server Extensions で発行するには、まず、FrontPage Server Extensions をインストールする必要があります。  インストールは、Windows Server の "サーバーの役割管理" ツールを使用して実行できます。  
  
## Windows Server: ロック ダウンされているコンテンツ タイプ  
 [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] の IIS では、一部の既知のコンテンツ タイプ \(.htm、.html、.txt など\) を除くすべてのファイルの種類がロック ダウンされています。  このサーバーを使用して [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを配置できるようにするには、種類が .application、.manifest のファイル、およびアプリケーションで使用しているその他のカスタム ファイルの種類のファイルをダウンロードできるように IIS の設定を変更する必要があります。  
  
 IIS サーバーを使用して配置する場合は、inetmgr.exe を実行し、既定の Web ページに新しいファイルの種類を追加します。  
  
-   .application 拡張子と .manifest 拡張子に対しては、MIME 型を "application\/x\-ms\-application" に設定する必要があります。その他のファイルの種類に対しては、MIME 型を "application\/octet\-stream" に設定する必要があります。  
  
-   拡張子 "\*" を新たに追加し、MIME 型を "application\/octet\-stream" に設定した場合、ブロックされていないファイルの種類のファイルをダウンロードできるようになります   \(ただし、.aspx や .asmx などのブロックされているファイルの種類はダウンロードできません\)。  
  
 Windows Server で MIME 型を構成する具体的な手順については、Microsoft サポート技術情報の文書 KB326965「不明な MIME の種類が IIS 6.0 で配信されない」\([http:\/\/support.microsoft.com\/default.aspx?scid\=kb;ja\-jp;326965](http://support.microsoft.com/default.aspx?scid=kb;ja-jp;326965)\) を参照してください。  
  
## コンテンツ タイプの割り当て  
 HTTP を使用して発行するときは、.application ファイルのコンテンツ タイプ \(MIME 型とも呼ばれます\) が "application\/x\-ms\-application" に設定されている必要があります。サーバーに [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] がインストールされている場合、この設定は自動的に行われます。  インストールされていない場合は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションの vroot \(またはサーバー全体\) に対して、MIME 型の関連付けを作成する必要があります。  
  
 IIS サーバーを使用して配置する場合は、inetmgr.exe を実行し、.application 拡張子に対して新しいコンテンツ タイプ "application\/x\-ms\-application" を追加します。  
  
## HTTP 圧縮に関する問題  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] では、HTTP 圧縮を使用した状態でファイルをダウンロードできます。HTTP 圧縮は、クライアントに送信するデータ ストリームを GZIP アルゴリズムで圧縮する Web サーバー テクノロジです。  クライアント \(この場合は [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\) では、ストリームを圧縮解除してからファイルを読み込みます。  
  
 IIS を使用している場合には、HTTP 圧縮を簡単に有効にできます。  ただし、HTTP 圧縮は、特定のファイルの種類 \(HTML ファイルとテキスト ファイル\) のみに対して有効になります。  アセンブリ \(.dll\)、XML \(.xml\)、配置マニフェスト \(.application\)、およびアプリケーション マニフェスト \(.manifest\) の圧縮を有効にするには、これらのファイルの種類を IIS で圧縮対象となるファイルの種類のリストに追加する必要があります。  配置に対してファイルの種類を追加するまでは、テキスト ファイルと HTML ファイルのみが圧縮されます。  
  
 IIS での詳細な手順については、「[HTTP 圧縮対象のドキュメントの種類を追加する方法](http://go.microsoft.com/fwlink/?LinkId=178459)」を参照してください。  
  
## 参照  
 [ClickOnce 配置のトラブルシューティング](../deployment/troubleshooting-clickonce-deployments.md)   
 [ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [アプリケーション配置の必要条件](../deployment/application-deployment-prerequisites.md)