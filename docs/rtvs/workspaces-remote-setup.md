---
title: "R Tools for Visual Studio でのリモート ワークスペース | Microsoft Docs"
ms.custom: 
ms.date: 4/27/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5778c9cf-564d-47b0-8d64-e5dc09162479
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 1016f07c0f4505f2dd652482dd4d568655565cf0
ms.contentlocale: ja-jp
ms.lasthandoff: 05/12/2017

---


# <a name="setting-up-remote-workspaces"></a>リモート ワークスペースの設定

R Tools for Visual Studio (RTVS) でリモート ワークスペースを使用するには、このトピックの説明に従って、SSL と適切な R サービスを使用してリモート コンピューターを構成する必要があります。 

- [リモート コンピューターの要件](#remote-computer-requirements)
- [SSL 証明書のインストール](#install-an-ssl-certificate)
- [R Services のインストール](#install-r-services)
- [R Services の構成](#configure-r-services)
- [トラブルシューティング](#troubleshooting)

## <a name="remote-computer-requirements"></a>リモート コンピューターの要件

- Windows 10、Windows Server 2016、または Windows Server 2012 R2。 RTVS には以下も必要です。
- [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) 以降

## <a name="install-an-ssl-certificate"></a>SSL 証明書のインストール

RTVS を使用するには、リモート サーバーとのすべての通信を HTTP 上で行う必要があります。また、サーバー上に SSL 証明書が必要です。 信頼できる証明機関が署名した証明書を使用する (推奨) か、自己署名証明書 (接続時に RTVS から警告が発行されます) を使用できます。 いずれの場合でも、コンピューター上に証明書をインストールし、その秘密キーにアクセスできるようにする必要があります。

### <a name="obtaining-a-trusted-certificate"></a>信頼できる証明書の取得

信頼できる証明書は、証明機関から発行されます (背景については、[Wikipedia の証明機関のページ](https://en.wikipedia.org/wiki/Certificate_authority)を参照してください)。 公的な身分証明書を入手する場合と同様に、信頼できる証明書の取得には多くのプロセスが必要で、料金がかかる可能性もありますが、要求と要求元の信頼性が検証されます。

証明書に含める必要がある重要なフィールドは、R サーバー コンピューターの完全修飾ドメイン名です。 証明機関に対して、サーバーが属するドメインに新しいサーバーを作成する権限を持っていることを証明する必要があります。

詳細な背景については、[Wikipedia の公開鍵証明書のページ](https://en.wikipedia.org/wiki/Public_key_certificate)を参照してください。

### <a name="obtaining-a-self-signed-certificate"></a>自己署名証明書の取得

信頼できる証明機関の証明書と比較すると、自己署名証明書は自分の身分証明書を作成するようなものです。 当然ながら、信頼できる証明機関の場合よりも作業は非常に単純ですが、強力な認証がありません。つまり、攻撃者が自分の証明書で未署名の証明書を上書きして、クライアントとサーバー間のすべてのトラフィックをキャプチャすることができます。 *そのため、自己署名証明書は、信頼できるネットワーク上で、テスト シナリオの場合に限定して使用し、運用環境には使用しないことが推奨されます。*

この理由から、自己署名証明書を使用してサーバーに接続しようとすると、RTVS からは常に次の警告が発行されます。

![自己署名証明書の警告ダイアログ](~/rtvs/media/workspaces-remote-self-signed-certificate-warning.png)

自己署名証明書を発行するには:

1. 管理者アカウントを使用して R サーバー コンピューターにログオンします。
1. 新しい管理者用 PowerShell コマンド プロンプトを開き、次のコマンドを発行します。その際に、`"remote-machine-name"` は実際のサーバー コンピューターの完全修飾ドメイン名で置き換えます。

    ```ps
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "remote-machine-name"
    ```

1. R サーバー コンピューター上でまだ PowerShell を実行したことがない場合は、次のコマンドを実行して、コマンドの実行を明示的に有効にする必要があります。

    ```ps
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    ```

背景については、[Wikipedia の自己署名証明書のページ](https://en.wikipedia.org/wiki/Self-signed_certificate)を参照してください。

### <a name="installing-the-certificate"></a>証明書のインストール

リモート コンピューターに証明書をインストールするには、コマンド プロンプトから `certlm.msc` (証明書マネージャー) を実行します。 **[個人]** フォルダーを右クリックし、**[すべてのタスク]、[インポート]** コマンドの順に選択します。

![証明書のインポート コマンド](~/rtvs/media/workspaces-remote-certificate-import.png)


### <a name="granting-permissions-to-read-the-ssl-certificates-private-key"></a>SSL 証明書の秘密キーを読み取るアクセス許可の付与

証明書をインポートしたら、以下の手順で秘密キーを読み取るアクセス許可を `NETWORK SERVICE` アカウントに付与します。 `NETWORK_SERVICE` は、R Services ブローカーの実行に使用されるアカウントです。R Services ブローカーは、サーバー コンピューターに対する受信 SSL 接続を終了するサービスです。

1. 管理者のコマンド プロンプトから `certlm.msc` (証明書マネージャー) を実行します。
1. **[個人] の [証明書]** を展開し、証明書を右クリックし、**[すべてのタスク]、[秘密キーの管理]** の順に選択します。
1. 証明書を右クリックし、[すべてのタスク] の [秘密キーの管理] コマンドを選択します。
1. 表示されるダイアログで **[追加]** を選択し、アカウント名として「`NETWORK SERVICE`」と入力します。

    ![[秘密キーの管理] ダイアログ、NETWORK_SERVICE の追加](~/rtvs/media/workspaces-remote-manage-private-key-dialog.png)

1. **[OK]** を 2 回選択してダイアログを閉じて変更を確定します。


## <a name="install-r-services"></a>R Services のインストール

R コードを実行するには、次のようにリモート コンピューターに R インタープリターがインストールされている必要があります。

1. 次のいずれかをダウンロードしてインストールします。

    - [Microsoft R Open](https://mran.microsoft.com/open/)
    - [CRAN R for Windows](https://cran.r-project.org/bin/windows/base/)

    いずれも機能は同じですが、Microsoft R Open の場合、さらにハードウェア アクセラレータによる [Intel Math Kernel Library](https://software.intel.com/intel-mkl) の線形代数ライブラリの提供を利用できます。

1. [R Services インストーラー](https://aka.ms/rtvs-services)を実行し、プロンプトが表示された場合は再起動します。 インストーラーは次の処理を行います。

    -    `%PROGRAMFILES%\R Tools for Visual Studio\1.0\` にフォルダーを作成し、必要なバイナリをすべてコピーします。
    -    `RHostBrokerService` と `RUserProfileService` をインストールし、自動起動するように構成します。
    -    自動起動するように `seclogon` サービスを構成します。
    -    既定のポート 5444 のファイアウォールの受信規則に `Microsoft.R.Host.exe` と `Microsoft.R.Host.Broker.exe` を追加します。

コンピューターを再起動すると、R Services は自動的に起動します。

- **R Host Broker Service** は、Visual Studio と、コンピューター上で R コードが実行されるプロセス間のすべての HTTPS トラフィックを処理します。
- **R User Profile Service** は、Windows ユーザー プロファイルの作成を処理する特権を持つコンポーネントです。 新しいユーザーが R サーバー コンピューターに初めてログオンしたときに呼び出されます。

これらの処理は、サービス管理コンソール (`compmgmt.msc`) で確認できます。  

## <a name="configure-r-services"></a>R Services の構成

リモート コンピューター上で R Services が実行されている場合、ユーザー アカウントを作成し、ファイアウォール規則を設定し、Azure ネットワークを構成し、SSL 証明書を構成する必要があります。

1. ユーザー アカウント: リモート コンピューターにアクセスする各ユーザーのアカウントを作成します。 標準の (特権のない) ローカル ユーザー アカウントを作成するか、R サーバー コンピューターをドメインに参加させて、適切なセキュリティ グループを `Users` セキュリティ グループに追加することができます。
1. ファイアウォール規則: `R Host Broker` の既定では、TCP ポート 5444 をリッスンしています。 そのため、受信トラフィックと送信トラフィックの両方に有効な Windows ファイアウォール規則があるようにします (送信は、パッケージのインストールなどのシナリオに必要です)。  組み込みの Windows ファイアウォールの場合、R Services インストーラーではこれらの規則が自動的に設定されます。 ただし、サードパーティのファイアウォールを使用している場合、`R Host Broker` 用のポート 5444 を手動で開く必要があります。
1. Azure の構成: リモート コンピューターが Azure 上の仮想マシンの場合、Windows ファイアウォールとは独立している Azure ネットワーク内の受信トラフィック用にもポート 5444 を開く必要があります。 詳細については、Azure ドキュメントの「[ネットワーク セキュリティ グループによるネットワーク トラフィックのフィルタリング](https://docs.microsoft.com/azure/virtual-network/virtual-networks-nsg)」を参照してください。
1. 読み込む SSL 証明書を R Host Broker に指示します。イントラネット サーバーに証明書をインストールしている場合、サーバーの完全修飾ドメイン名は NETBIOS 名と同じ可能性があります。 この例では、読み込まれている既定の証明書なので、実行が必要なことはありません。

    ただし、インターネットに接続するサーバー (Azure VM など) に証明書をインストールしている場合、サーバーの完全修飾ドメイン名 (FQDN) を使用します。これは、インターネットに接続するサーバーの FQDN が NETBIOS 名と同じではなくなるためです。

    FQDN を使用するには、R Services がインストールされている場所 (既定では `%PROGRAM FILES%\R Remote Service for Visual Studio\1.0`) に移動し、テキスト エディターで `Microsoft.R.Host.Broker.Config.json` ファイルを開き、内容を次のように置き換え、CN をいずれかのサーバーの FQDN (`foo.westus.cloudapp.azure.com` など) に割り当てます。

    ```json
    {
      "server.urls": "https://0.0.0.0:5444",
      "security": {
        "X509CertificateName": "CN=your-server-fully-qualified-domain-name"
      }
    }
    ```

    ファイルを保存し、コンピューターを再起動して変更を適用します。

## <a name="troubleshooting"></a>トラブルシューティング

**R サーバー コンピューターが応答していません。どうすればよいですか?**

コマンド ラインからリモート コンピューターに対して `ping remote-machine-name` を実行して成功するかどうかを確認します。 ping に失敗する場合、コンピューターが実行されていることを確認します。

**Q.[R インタラクティブ] ウィンドウにリモート コンピューターは起動中と表示されますが、サービスが実行されないのはなぜですか?**

これには、次の理由が考えられます。

-    [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) 以降がコンピューターにインストールされていません。
-    ポート 5444 上の受信接続と送信接続の両方について、`Microsoft.R.Host.Broker` と `Microsoft.R.Host` のファイアウォール規則が有効ではありません。
-    `CN=<remote-machine-name>` の SSL 証明書がインストールされていませんでした。

上記の変更を行った後にコンピューターを再起動します。 次に、タスク マネージャー ([サービス] タブ) または `services.msc` で `RHostBrokerService` と `RUserPofileService` が実行されていることを確認します。

**Q.R サーバーに接続しているときに、[R インタラクティブ] ウィンドウに "401 アクセスは拒否されました" と表示されるのはなぜですか?**

考えられる理由は 2 つあります。

- 高い可能性で、`NETWORK SERVICE` アカウントが SSL 証明書の秘密キーへのアクセス権を持っていません。 前述の手順に従って、`NETWORK SERVICE` に秘密キーへのアクセス権を付与してください。
- `seclogon` サービスが実行されていることを確認します。 `services.msc` を使用して、`seclogon` が自動起動するように構成します。                                                         
**Q.R サーバーに接続しているときに、[R インタラクティブ] ウィンドウに "404 見つかりません" と表示されるのはなぜですか?**

おそらく、Visual C++ 再頒布可能ライブラリが存在しないことが原因です。 [R インタラクティブ] ウィンドウで、ライブラリ (DLL) の不足に関するメッセージがあるかどうかを確認します。 次に、VS 2015 再頒布可能ファイルがインストールされ、R もインストールされていることを確認します。

**Q.[R インタラクティブ] ウィンドウからインターネット/リソースにアクセスできません。どうすればよいですか?**

`Microsoft.R.Host.Broker` と `Microsoft.R.Host` のファイアウォール規則で、ポート 5444 上の送信アクセスを許可します。 変更の適用後にコンピューターを再起動します。

**Q.上記のすべてを試しても問題が解決しません。どうすればよいですか?**

`C:\Windows\ServiceProfiles\NetworkService\AppData\Local\Temp` 内のログ ファイルを確認してください。 実行されていた R Broker Service のインスタンスごとに別のログ ファイルがあります。 つまり、何らかの理由でサービスを再起動する必要があった場合は、新しいログ ファイルが作成されます。 発生した可能性がある問題の手がかりについては、最新のタイムスタンプのログ ファイルを確認することをお勧めします。

