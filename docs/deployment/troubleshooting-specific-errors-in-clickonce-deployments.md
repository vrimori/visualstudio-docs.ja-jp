---
title: ClickOnce 配置で特定のエラーのトラブルシューティング |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: b52caad3b6e4c98dd78e6c6be9835c11ac4d4175
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshooting-specific-errors-in-clickonce-deployments"></a>ClickOnce 配置の固有のエラーのトラブルシューティング
このトピックの一覧を展開するときに発生する可能性がある次の一般的なエラー、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションでは、各問題を解決する手順を示します。  
  
## <a name="general-errors"></a>一般的なエラー  
  
#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>ときに何も行われません、.application ファイルを検索しようとする Internet Explorer で、XML を表示または実行または名前を付けて保存 ダイアログ ボックスが表示されます。  
 このエラーは、サーバーまたはクライアントに正しく登録されていないコンテンツ タイプ (MIME の種類とも呼ばれます) による可能性があります。  
  
 まずにコンテンツの種類「/x ms-アプリケーション」は .application という拡張子を関連付けるには、サーバーが構成されていることを確認します。  
  
 場合は、サーバーが正しく構成されていることを確認、[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]がお使いのコンピューターにインストールされています。 場合、[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]がインストールされていて、まだこの問題をアンインストールして再インストールしてください、[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]クライアントでコンテンツの種類を再登録します。  
  
#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>エラー メッセージでは、"アプリケーションを取得できません。 ファイルの展開が見つかりません"または「アプリケーションのダウンロードが中断されて、ネットワーク エラーを確認し、後でもう一度やり直してください」  
 このメッセージが示すによって参照される 1 つまたは複数のファイル、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]マニフェストをダウンロードすることはできません。 このエラーをデバッグする最も簡単な方法は、URL をダウンロードしようとするを[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]ダウンロードできないと表示されます。 考えられる原因を次に示します。  
  
-   かどうか、ログ ファイルは「(403) アクセス不可」または"(404) Not found"は、このファイルのダウンロードをブロックしないようにする Web サーバーが構成されていることを確認します。 詳細については、「[ClickOnce 配置でのサーバーおよびクライアント構成の問題](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md)」を参照してください。  
  
-   、.Config ファイルがサーバーによってブロックされている場合は、セクションを参照してください。"インストールしようとすると、エラーをダウンロード、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .config ファイルを持つアプリケーション"このトピックで後述します。  
  
-   このため発生するかどうかを判断、`deploymentProvider`配置マニフェストで URL がアクティブ化に使用される URL とは異なる場所を指しています。  
  
-   すべてのファイルがサーバーに存在することを確認します。[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]ログで確認してくださいのどのファイルが見つかりませんでした。  
  
-   ネットワーク接続の問題があるかどうかを参照してください。ダウンロード中に、クライアント コンピューターがオフラインになった場合、このメッセージが表示されることができます。  
  
#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>.Config ファイルを持つ ClickOnce アプリケーションをインストールしようとすると、エラーをダウンロードします。  
 既定では、Visual Basic の Windows ベースのアプリケーションには、App.config ファイルが含まれています。 問題があるユーザーはそのオペレーティング システムがセキュリティ上の理由の .config ファイルのインストールをブロックしているために、Windows Server 2003 を使用する Web サーバーからインストールしようとしています。 インストールする、.config ファイルを有効にする をクリックして**".deploy"ファイル拡張子を使用して**で、**発行オプション** ダイアログ ボックス。  
  
 設定することも必要がありますコンテンツ タイプ (MIME の種類とも呼ばれます) は、適切に .application、マニフェスト、および .deploy のファイルです。 詳細については、Web サーバーのマニュアルを参照してください。  
  
 詳細については、「Windows Server 2003:: ロックダウンされたコンテンツの種類」を参照してください[サーバーおよび ClickOnce の配置内のクライアント構成の問題](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md)です。  
  
#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>エラー メッセージ:「アプリケーションの形式が正しくありません」です。ログ ファイルには、「XML 署名が正しくありません」が含まれています。  
 マニフェスト ファイルを更新してときに再署名することを確認します。 使用して、アプリケーションを再発行[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]か Mage を使用して、アプリケーションに再署名します。  
  
#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>サーバーで、アプリケーションを更新したが、クライアントが更新をダウンロードしません。  
 この問題は、次のタスクのいずれかの手順で解決可能性があります。  
  
-   確認、`deploymentProvider`配置マニフェストで URL。 同じ場所に bits を更新していることを確認する`deploymentProvider`を指します。  
  
-   配置マニフェストの更新間隔を確認します。 この間隔は、6 時間に 1 回など、定期的な間隔に設定されている場合[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]はこの間隔が経過するまでに更新プログラムをスキャンしません。 アプリケーションを起動するたびに更新プログラムをスキャンするマニフェストを変更することができます。 更新間隔の変更は、開発時に更新プログラムがインストールされているが、アプリケーションのアクティベーションが長くなることを確認する便利なオプションです。  
  
-   [スタート] メニュー、アプリケーションをもう一度開始してください。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] バック グラウンドで更新を検出した可能性がありますが、次回の起動時に、bits をインストールするように求められます。  
  
#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>更新中に次のログ エントリがあるエラーを受信します"配置内の参照と一致しません、アプリケーション マニフェストで定義されている id"。  
 配置マニフェストとアプリケーション マニフェスト、手動で編集して、他の同期するように 1 つのマニフェストにアセンブリの id の説明が原因となったので、このエラーが発生する可能性があります。 アセンブリの id は、その名前、バージョン、カルチャ、および公開キー トークンで構成されます。 マニフェストの id の記述を確認し、すべての差異を解決します。  
  
#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>最初にローカル ディスクまたは CD-ROM からのアクティブ化は成功しますが、[スタート] メニューからの後続のライセンス認証が成功しなかった  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置プロバイダー URL を使用して、アプリケーションの更新プログラムを受信します。 URL が指している場所が正しいことを確認します。  
  
#### <a name="error-cannot-start-the-application"></a>エラー:「アプリケーションを起動できません」  
 このエラー メッセージが通常にこのアプリケーションのインストールに関する問題があることを示す、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]を格納します。 アプリケーションにエラーがあるか、ストアが破損しています。 ログ ファイルがありますを伝えるエラーが発生したです。  
  
 次の操作を行う必要があります。  
  
-   配置マニフェストの id、アプリケーション マニフェストの id、およびメインのアプリケーション EXE の id がすべて一意であることを確認します。  
  
-   ファイルのパスが 100 文字を超えていないことを確認します。 ファイルのパスが長すぎる場合は、保存できるパスの最大の制限を超える可能性があります。 再インストールして、パスを短くしてください。  
  
#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>アプリケーション構成ファイルに PrivatePath 設定は適用されません。  
 PrivatePath (Fusion のプローブ パス) を使用するのには、アプリケーションが完全信頼のアクセス許可を要求する必要があります。 完全な信頼を要求してから、再試行をアプリケーション マニフェストを変更してください。  
  
#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>アンインストール中に、メッセージが表示されるという、「アプリケーションのアンインストールに失敗しました」  
 このメッセージは、通常、アプリケーションが既に削除されてか、ストアが破損していることを示します。 クリックした後**OK**、**プログラムの追加/削除**エントリが削除されます。  
  
#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>インストール中に、メッセージがプラットフォームの依存関係がインストールされていないことを示す表示されます。  
 アプリケーションが実行するために必要のある GAC (グローバル アセンブリ キャッシュ) の前提条件がありません。  
  
## <a name="publishing-with-visual-studio"></a>Visual Studio を使用した発行  
  
#### <a name="publishing-in-visual-studio-fails"></a>Visual Studio での発行に失敗しました。  
 あるサーバーにパブリッシュする権限を対象とすることを確認します。 たとえば、ターミナル サーバー コンピューターに管理者としてではなく、通常のユーザーとしてログインしている場合おそらく必要はありませんローカル Web サーバーへの公開に必要な権限。  
  
 URL を使用して発行する場合は、セットアップ先のコンピューターは、FrontPage Server Extensions が有効であることを確認します。  
  
#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>エラー メッセージ: Web サイトを作成できません。 '\<サイト >' です。 FrontPage Server Extensions と通信するためのコンポーネントがインストールされていません。  
 Microsoft Visual Studio Web オーサリング コンポーネントから公開しているコンピューターにインストールできることを確認します。 Express のユーザーの既定ではこのコンポーネントはインストールされていません。 詳細については、「[http://go.microsoft.com/fwlink/?LinkId=102310](http://go.microsoft.com/fwlink/?LinkId=102310)」を参照してください。  
  
#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>エラー メッセージ: ファイルが見つかりませんでした ' Microsoft.Windows.Common-コントロール、バージョン = 6.0.0.0、カルチャ = *、PublicKeyToken = 6595b64144ccf1df、ProcessorArchitecture =\*型 = win32'  
 有効になっている visual スタイルを WPF アプリケーションを発行しようとしたときに、このエラー メッセージが表示されます。 この問題を解決するには、次を参照してください。[する方法: Visual スタイルが有効なに WPF アプリケーションを発行](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)です。  
  
## <a name="using-mage"></a>Mage を使用します。  
  
#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>証明書ストアと、受信した空白のメッセージ ボックスで証明書に署名しようとしています。  
 **署名**ダイアログ ボックスで、する必要があります。  
  
-   選択**保存された証明書を使用してサインイン**、および  
  
-   証明書一覧から選択します。最初の証明書は、既定の選択ではないです。  
  
#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>「署名のない」ボタンをクリックすると、例外が発生します。  
 この問題は、既知のバグです。 すべて[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]マニフェストに署名する必要があります。 署名のオプションのいずれかを選択し、をクリックして**OK**です。  
  
## <a name="additional-errors"></a>その他のエラー  
 次の表は、クライアント コンピューターのユーザーがユーザーをインストールするときに表示される一般的なエラー メッセージ、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションです。 エラーの最も考えられる原因の説明の横にある各エラー メッセージが表示されます。  
  
|エラー メッセージ|説明|  
|-------------------|-----------------|  
|アプリケーションを起動できません。 アプリケーションの発行元に問い合わせてください。<br /><br /> アプリケーションを起動できません。 について、アプリケーション ベンダーに問い合わせてください。|これらは、アプリケーションを開始することはできません、および他の特別な理由が見つからないときに発生する一般的なエラー メッセージです。 または、アプリケーションが何らかの理由で破損しているため頻繁を[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]ストアが壊れています。|  
|続行できません。 アプリケーションの形式が正しくありません。 サポートが必要なアプリケーションの発行元に問い合わせてください。<br /><br /> アプリケーションの検証は成功しませんでした。 続行できません。<br /><br /> アプリケーション ファイルを取得できません。 展開内のファイルが壊れています。|展開内のマニフェスト ファイルのいずれかの構文が無効、または、対応するファイルを使用して調整することはできません、ハッシュが含まれています。 このエラーは、アセンブリに埋め込まれたマニフェストが破損していることも可能性があります。 配置を再作成し、アプリケーションを再コンパイルまたはを検出し、マニフェストのエラーを手動で修正します。|  
|アプリケーションを取得することはできません。 認証エラーです。<br /><br /> アプリケーションのインストールは成功しませんでした。 サーバー上のアプリケーション ファイルを見つけることができません。 アプリケーションの発行元または管理者に問い合わせてください。|必要なアクセス許可があるないために、展開内の 1 つまたは複数のファイルをダウンロードできません。 これは、保護されたファイルとして扱う Web サーバーにする拡張機能の配置内のファイルのいずれかが終了した場合に発生する可能性があります Web サーバーによって返される 403 Forbidden エラーによって可能性があります。 また、1 つ以上のアプリケーションのファイルを格納するディレクトリ必要があります、ユーザー名とパスワードにアクセスするために。|  
|アプリケーションをダウンロードすることはできません。 アプリケーションには、必要なファイルがありません。 について、アプリケーション ベンダーやシステム管理者に問い合わせてください。|1 つ以上のアプリケーション マニフェストに示されているファイルがサーバー上に見つかりません。 配置のすべての依存ファイルをアップロードし、もう一度やり直してくださいを確認します。|  
|アプリケーションのダウンロードに失敗しました。 ネットワーク接続を確認またはシステム管理者またはネットワーク サービス プロバイダーに問い合わせてください。|[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] サーバーへのネットワーク接続を確立できません。 サーバーの可用性とネットワークの状態を確認します。|  
|URLDownloadToCacheFile を HRESULT で失敗しました。 '\<番号 >' です。 ダウンロードしようとしてエラーが発生しました '\<ファイル >' です。|場合は、ユーザーが設定 Internet Explorer の高度なセキュリティ オプション「セキュリティで保護を切り替える場合に警告する し、保護モード」配置対象のコンピューターに、セキュリティで保護されたサイトにインストールされる ClickOnce アプリケーションのセットアップの URL がリダイレクトから保護されていない場合 (またはその逆)、Internet Explorer の警告で中断されるため、インストールは失敗します。<br /><br /> これを解決するには、次のいずれかの操作を行います。<br /><br /> セキュリティ オプションをオフにします。<br />-セットアップ URL がセキュリティ モードを変更する方法でリダイレクトされないことを確認します。<br />リダイレクトを完全に削除し、実際のセットアップの URL をポイントします。|  
|エラーには、ハード ディスクへの書き込みが発生しました。 場合もある十分な空き領域、ディスクにします。 について、アプリケーション ベンダーやシステム管理者に問い合わせてください。|これは、アプリケーションを格納するための十分なディスク領域を示している可能性がありますが、アプリケーション ファイルをディスク ドライブに保存しようとするより一般的な I/O エラーを示す場合もします。|  
|アプリケーションを起動できません。 ディスク上に十分な空き領域がありません。|ハード ディスクがいっぱいです。 空き領域を確保して、アプリケーションを再実行を再試行してください。|  
|多すぎます配置済みのライセンス認証は、同時に読み込みしようとしています。|[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 同時に開始できる別のアプリケーションの数を制限します。 これは、主に、悪意のある処置ローカルに対するサービス拒否攻撃から保護するため[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]サービス以外のユーザーがすばやく連続的に繰り返し、同じアプリケーションを起動しようと、単一のインスタンスは終了のみ、アプリケーション。|  
|ショートカットは、ネットワーク経由でアクティブにできません。|ショートカットを[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションは、ローカルのハード_ディスクにのみ開始できます。 リモート サーバー上のショートカット ファイルを指す URL を開くことによって、開始できません。|  
|部分信頼でオンラインを実行するには、アプリケーションが大きすぎます。 について、アプリケーション ベンダーやシステム管理者に問い合わせてください。|部分信頼で実行されるアプリケーションは、既定では、250 MB のオンライン アプリケーションのクォータのサイズの半分より大きくすることはできません。|  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce 配置のトラブルシューティング](../deployment/troubleshooting-clickonce-deployments.md)