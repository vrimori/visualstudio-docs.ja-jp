---
title: ClickOnce 配置で特定のエラーのトラブルシューティング |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.UncRequired
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.NoInstallUrl
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
ms.assetid: 22dfe8f1-8271-4708-9c25-6bbb13920ac8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b738a419c93e1741fd2567fb18c9998beb181bd7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040633"
---
# <a name="troubleshoot-specific-errors-in-clickonce-deployments"></a>ClickOnce 配置の固有のエラーのトラブルシューティング
この記事では、展開するときに発生する可能性がある次の一般的なエラーを示します、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションでは、各問題を解決する手順を示します。  

## <a name="general-errors"></a>一般的なエラー  

#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>ときに何も問題が発生すると、アプリケーション ファイルを検索しようとするまたは Internet Explorer で、XML を表示または実行または名前を付けて保存 ダイアログ ボックスが表示されます。  
 このエラーは、サーバーまたはクライアントに正しく登録されていないコンテンツの種類 (MIME の種類とも呼ばれます) による可能性があります。  

 まずに関連付けるサーバーが構成されていることを確認、 *.application*コンテンツを含む拡張機能の種類「/x ms-アプリケーションです」。  

 場合は、サーバーが正しく構成されていることを確認、[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]がコンピューターにインストールされています。 場合、[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]がインストールされているアンインストールと再インストールしてみてください、この問題が引き続き発生して、[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]クライアントでコンテンツの種類を再登録します。  

#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>エラー メッセージでは、"アプリケーションを取得できません。 ファイルの展開が見つかりません"または「アプリケーションのダウンロードが中断された、ネットワーク エラーを確認し、後でもう一度お試しください」  
 このメッセージを示すによって参照される 1 つまたは複数のファイル、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]マニフェストをダウンロードすることはできません。 このエラーをデバッグする最も簡単な方法は、URL をダウンロードしようとするする[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]をダウンロードできないことを示します。 考えられる原因を次に示します。  

- かどうか、ログ ファイルは "(403) Forbidden"または"(404) Not found"がこのファイルのダウンロードをブロックしないようにする Web サーバーが構成されていることを確認します。 詳細については、「[ClickOnce 配置でのサーバーおよびクライアント構成の問題](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md)」を参照してください。  

- 場合、 *.config*ファイルがサーバーによってブロックされてを参照してください"をインストールしようとすると、エラーをダウンロード、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .config ファイルがあるアプリケーション"この記事で後述します。  

- に、このエラーが発生したかどうかを判断、`deploymentProvider`配置マニフェストで URL がアクティブ化に使用する URL とは異なる場所を指しています。  

- すべてのファイルがサーバー上に存在することを確認します。[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]ログがどのように指示するファイルが見つかりませんでした。  

- ネットワーク接続の問題があるかどうかを参照してください。ダウンロード中に、クライアント コンピューターがオフラインになった場合、このメッセージが表示されることができます。  

#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>.Config ファイルがある ClickOnce アプリケーションをインストールしようとすると、エラーをダウンロードします。  
 既定では、Visual Basic の Windows ベースのアプリケーションには、App.config ファイルが含まれています。 問題があるユーザーが、そのオペレーティング システムのインストールをブロックしているため、Windows Server 2003 を使用する Web サーバーからインストールしようとしています。 *.config*ファイル セキュリティ上の理由。 有効にする、 *.config*インストールには、をクリックしてファイル **".deploy"ファイル拡張子を使用して、** で、**発行オプション** ダイアログ ボックス。  

 設定することも必要があります、コンテンツの種類 (MIME の種類とも呼ばれます) は、適切の .application、.manifest、および .deploy ファイル。 詳細については、Web サーバーのマニュアルを参照してください。  

 詳細については、次を参照してください。"Windows Server 2003。ロックされたコンテンツの種類" [ClickOnce 配置でサーバーとクライアントの構成に関する問題](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md)します。  

#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>エラー メッセージ「アプリケーションの形式が正しくありません」。ログ ファイルには、「XML 署名が無効です」が含まれています。  
 マニフェスト ファイルを更新して、再度署名されたことを確認してください。 使用して、アプリケーションを再発行[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]または Mage を使用して、もう一度アプリケーションに署名します。  

#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>サーバーで、アプリケーションの更新が、クライアントは、更新プログラムをダウンロードしていません。  
 次のタスクのいずれかを実行して、この問題を解決可能性があります。  

- 確認、`deploymentProvider`配置マニフェストの URL。 同じ場所に bits を更新することを確認する`deploymentProvider`を指します。  

- 配置マニフェストの更新間隔を確認します。 この間隔が 1 回、6 時間ごとなどの定期的な間隔に設定されている場合[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]はこの間隔が経過するまでに更新プログラムをスキャンしません。 アプリケーションを起動するたびに更新プログラムをスキャンするマニフェストを変更することができます。 更新間隔の変更は、開発時に更新プログラムがインストールされているアプリケーションのアクティベーションが長くなることを確認する便利なオプションです。  

- [スタート] メニューにアプリケーションをもう一度起動してみてください。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] バック グラウンドで更新を検出した可能性がありますが、次回の起動時に、bits をインストールするように求められます。  

#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>更新中には、次のログ エントリがあるエラーが表示されます。「デプロイメント内の参照は、アプリケーション マニフェストで定義されている id に一致しない」  
 展開およびアプリケーション マニフェストでは、手動で編集し、両者を同期するように 1 つのマニフェストにアセンブリの id の説明が原因となったために、このエラーが発生する可能性があります。 アセンブリの id は、その名前、バージョン、カルチャ、および公開キー トークンで構成されます。 マニフェストの identity の説明を確認し、任意の相違点を修正します。  

#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>最初にローカル ディスクまたは CD-ROM からのアクティブ化は成功しますが、[スタート] メニューからの後続のアクティベーションが成功しなかった  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置プロバイダーの URL を使用して、アプリケーションの更新プログラムを受信します。 URL を指している場所が正しいことを確認します。  

#### <a name="error-cannot-start-the-application"></a>エラー :「アプリケーションを起動できません」  
 このエラー メッセージが通常にこのアプリケーションのインストールに問題があることを示して、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]を格納します。 アプリケーション エラーがあるか、ストアが破損しています。 ログ ファイルわかる場合がありますエラーが発生しました。  

 次の操作を行う必要があります。  

-   配置マニフェストの id、アプリケーション マニフェストの id、およびメイン アプリケーションの EXE の id がすべて一意であることを確認します。  

-   ファイルのパスが 100 文字を超えていないことを確認します。 アプリケーションには長すぎるファイル パスが含まれている場合は、格納できるパスの最大の制限を超える可能性があります。 再インストールして、パスを短くしてください。  

#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>アプリケーション構成ファイルで PrivatePath 設定は適用されません。  
 PrivatePath (Fusion のプローブ パス) を使用するには、アプリケーションは、完全な信頼のアクセス許可を要求する必要があります。 完全な信頼を要求し、もう一度お試しに、アプリケーション マニフェストを変更してください。  

#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>アンインストール中にメッセージを表示するという、「アプリケーションのアンインストールに失敗しました」  
 このメッセージは、通常、アプリケーションが既に削除されているか、ストアが破損していることを示します。 クリックした後**OK**、**プログラムの追加/削除**エントリが削除されます。  

#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>インストール中に、メッセージがプラットフォームの依存関係がインストールされていないことを示す表示されます。  
 アプリケーションを実行するために必要のある GAC (グローバル アセンブリ キャッシュ) の前提条件がありません。  

## <a name="publishing-with-visual-studio"></a>Visual Studio を使用した発行  

#### <a name="publishing-in-visual-studio-fails"></a>Visual Studio での発行が失敗しました。  
 あるか、サーバーに発行する権利を対象となることを確認します。 たとえば、ターミナル サーバー コンピューター管理者としてではなく、通常のユーザーとしてログインしている場合おそらくはありません、ローカル Web サーバーへの公開に必要な権限。  

 URL を使用してパブリッシュする場合は、セットアップ先のコンピューターに有効になっている FrontPage Server Extensions を確認します。  

#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>エラー メッセージWeb サイトを作成できません。 '\<サイト >'。 FrontPage Server Extensions と通信するためのコンポーネントがインストールされていません。  
 Microsoft Visual Studio Web Authoring コンポーネントから公開しているコンピューターにインストールされているがあることを確認します。 Express ユーザーは、このコンポーネントは、既定ではインストールされません。 詳細については、「[http://go.microsoft.com/fwlink/?LinkId=102310](http://go.microsoft.com/fwlink/?LinkId=102310)」を参照してください。  

#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>エラー メッセージファイルが見つかりませんでした ' Microsoft.Windows.Common-コントロール、バージョン 6.0.0.0、カルチャを = = *、PublicKeyToken = 6595b64144ccf1df、ProcessorArchitecture =\*型 = win32'  
 Visual スタイルが有効になっている WPF アプリケーションを発行しようとしたときに、このエラー メッセージが表示されます。 この問題を解決するには、次を参照してください。[方法。Visual スタイルが有効になっている WPF アプリケーションの発行](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)  

## <a name="using-mage"></a>Mage を使用します。  

#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>証明書ストアと空白のメッセージを受信したボックス内の証明書に署名しようとしています。  
 **署名** ダイアログ ボックスがあります。  

-   選択**格納された証明書を使用してサインイン**と  

-   は、一覧から証明書を選択します。最初の証明書は、既定で選択します。  

#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>「署名のない」ボタンをクリックすると、例外が発生します。  
 この問題は、既知のバグです。 すべて[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]マニフェストが署名するために必要です。 署名のオプションのいずれかを選択し、 **OK**します。  

## <a name="additional-errors"></a>その他のエラー  
 次の表は、クライアント コンピューターのユーザーがインストールするときに表示される一般的なエラー メッセージ、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション。 エラーの最も考えられる原因の説明の横にある各エラー メッセージが表示されます。  


| エラー メッセージ | 説明 |
| - | - |
| アプリケーションを開始できません。 アプリケーションの発行元にお問い合わせください。<br /><br /> アプリケーションを起動することはできません。 について、アプリケーション ベンダーに問い合わせてください。 | これらは、アプリケーションを起動することはできませんし、その他の特定の理由が見つからないときに発生する一般的なエラー メッセージです。 または、アプリケーションが何らかの理由で破損しているこの手段頻繁に、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]ストアが破損しています。 |
| 続行できません。 アプリケーションは形式が正しくありません。 については、アプリケーションの発行元にお問い合わせください。<br /><br /> アプリケーションの検証は成功しませんでした。 続行できません。<br /><br /> アプリケーション ファイルを取得できません。 展開では、ファイルが壊れています。 | 展開内のマニフェスト ファイルの 1 つは構文が無効ですが、または対応するファイルと一致することはできませんが、ハッシュが含まれています。 このエラーは、アセンブリに埋め込まれたマニフェストが破損していることもある可能性があります。 配置を再作成し、アプリケーションを再コンパイルまたは検索し、マニフェストに手動でのエラーを修正します。 |
| アプリケーションを取得することはできません。 認証エラーです。<br /><br /> アプリケーションのインストールは成功しませんでした。 サーバー上のアプリケーション ファイルを見つけることはできません。 についてアプリケーションの発行元または管理者に問い合わせてください。 | 展開内の 1 つまたは複数のファイルは、それらにアクセスする権限があるないために、ダウンロードできません。 拡張子が保護されたファイルとして扱う Web サーバーは、配置内のファイルのいずれかが終了した場合に発生する可能性があります Web サーバーによって返される 403 Forbidden エラーの可能性があります。 また、1 つまたは複数のアプリケーションのファイルを格納するディレクトリを必要がありますユーザー名とパスワードにアクセスするためにします。 |
| アプリケーションをダウンロードすることはできません。 アプリケーションには、必要なファイルがありません。 について、アプリケーション ベンダーまたはシステム管理者に問い合わせてください。 | 1 つ以上のアプリケーション マニフェストに示されているファイルがサーバー上に見つかりません。 配置のすべての依存ファイルをアップロードし、もう一度お試しことを確認します。 |
| アプリケーションのダウンロードは成功しませんでした。 ネットワーク接続を確認するか、システム管理者またはネットワーク サービス プロバイダーにお問い合わせください。 | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] サーバーへのネットワーク接続を確立することはできません。 サーバーの可用性とネットワークの状態を確認します。 |
| URLDownloadToCacheFile HRESULT により失敗しました '\<数 >'。 ダウンロードしようとしてエラーが発生しました '\<ファイル >'。 | "ユーザーが Internet Explorer の高度なセキュリティ オプション セキュリティで保護された間を変更する場合は、警告と設定モードをセキュリティで保護"展開対象のコンピューターにし、保護されていないからセキュリティで保護されたサイトにインストールされる ClickOnce アプリケーションのセットアップの URL がリダイレクトされる場合 (または逆に)、Internet Explorer の警告が発生してそのため、インストールは失敗します。<br /><br /> このエラーを解決するには、次のタスクのいずれかの操作を行います。<br /><br /> -セキュリティ オプションをオフにします。<br />-セットアップ URL がセキュリティ モードを変更するようにリダイレクトされないことを確認します。<br />リダイレクトを完全に削除し、実際のセットアップの URL をポイントします。 |
| ハード ディスクへの書き込みエラーが発生しました。 ある可能性があります領域が不足して利用可能なディスクにします。 について、アプリケーション ベンダーまたはシステム管理者に問い合わせてください。 | アプリケーションを格納するための十分なディスク領域がある可能性が、アプリケーション ファイルをディスク ドライブに保存しようとしているときに一般的な I/O エラーを示す場合もします。 |
| アプリケーションを起動することはできません。 ディスクに十分な空き領域がありません。 | ハード ディスクがいっぱいです。 空き領域を確保し、もう一度アプリケーションを実行しようとしてください。 |
| デプロイが多すぎるのライセンス認証を同時にロードしようとしています。 | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 同時に開始できるさまざまなアプリケーションの数を制限します。 これは、主に、悪意のある処置ローカルに対するサービス拒否攻撃から保護するため[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]; サービス ユーザーが立て続けに繰り返し、同じアプリケーションを起動しようと、1 つのインスタンスのみ結局は、アプリケーション。 |
| ショートカットは、ネットワーク経由でアクティブ化することはできません。 | ショートカットを[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションは、ローカルのハード_ディスクでのみ開始できます。 リモート サーバー上のショートカット ファイルを指す URL を開き、開始できません。 |
| 部分信頼でオンラインで実行するには、アプリケーションが大きすぎます。 について、アプリケーション ベンダーまたはシステム管理者に問い合わせてください。 | 部分信頼で実行されるアプリケーションは、online アプリケーション クォータは、既定では、250 mb のサイズの半分より大きくすることはできません。 |

## <a name="see-also"></a>関連項目  
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce 配置のトラブルシューティング](../deployment/troubleshooting-clickonce-deployments.md)
