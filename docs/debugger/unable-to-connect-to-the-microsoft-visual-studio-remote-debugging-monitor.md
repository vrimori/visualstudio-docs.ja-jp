---
title: "Microsoft Visual Studio リモート デバッグ モニターに接続できません |。Microsoft ドキュメント"
ms.custom: 
ms.date: 08/24/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.error.remote_debug
- vs.debug.error.firewall.remotemachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: a1d959fc-3817-491c-831b-e6b768a3877a
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 1d4298d60886d8fe8b402b59b1838a4171532ab1
ms.openlocfilehash: 454e6919c2f2bcd56153eb222fbf59b1ddc1080e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Microsoft Visual Studio リモート デバッグ モニターに接続できません。
このメッセージは、リモート デバッグ モニターが正しく設定されていないリモート コンピューター上またはリモート コンピューターがネットワークの問題またはファイアウォールが存在するためにアクセスできなくなっているために発生する可能性があります。
  
> [!IMPORTANT]
>  製品のバグによりこのメッセージが表示されている場合は、次のようにしてください。[この問題を報告](../ide/how-to-report-a-problem-with-visual-studio-2017.md)Visual Studio にします。 その他の支援が必要な場合は、Microsoft へのお問い合わせ方法について、「 [Talk to Us](../ide/talk-to-us.md) 」を参照してください。

## <a name="specificerrors"></a>詳細なエラー メッセージとは何ですか。

`Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor`メッセージはジェネリックです。 通常、詳細メッセージがエラーの文字列に含まれ、可能性がありますより正確な修正プログラムの検索、問題の原因を特定します。 次より一般的なエラー メッセージをメインのエラー メッセージに追加されたいくつかを示します。

- [デバッガーは、リモート コンピューターに接続できません。デバッガーは、指定したコンピューター名を解決するのにはできませんでした。](#cannot_connect)
- [接続要求は、リモート デバッガーによって拒否されました](#rejected)
- [メモリ位置への正しくないアクセス](#invalid_access)
- [指定された名前、リモート コンピューターで実行されているサーバーは存在しません](#no_server)
- [要求された名前が有効では、要求された型のデータが見つかりません](#valid_name)
- [ターゲット コンピューターに Visual Studio リモート デバッガーは、このコンピューターに接続できません。](#cant_connect_back)
- [アクセスが拒否されました](#access_denied)
- [セキュリティ パッケージの特定のエラーが発生しました](#security_package)

## <a name="cannot_connect"></a>デバッガーは、リモート コンピューターに接続できません。 デバッガーは、指定したコンピューター名を解決するのにはできませんでした。

次の手順を試してください。

1. 有効なコンピューターの名前を入力し、ポートの番号を確認してください、**プロセスにアタッチする**] ダイアログ ボックスまたは [プロジェクトのプロパティ (プロパティを設定するを参照してください。[手順](#server_incorrect))。 コンピューター名は、次の形式である必要があります。

    `computername:port`

    > [!NOTE]
    > ポート番号に一致する必要があります、[リモート デバッガーのポート番号](../debugger/remote-debugger-port-assignments.md)、どの*実行されている必要があります*対象コンピューターにします。

2. コンピューター名が機能しない場合は、IP アドレスし、ポート番号を代わりに。

3. ターゲット コンピューターで実行されているリモート デバッガーのバージョンが Visual Studio のバージョンと一致していることを確認してください。 リモート デバッガーの正しいバージョンを取得するには、次を参照してください。[リモート デバッグ](../debugger/remote-debugging.md)です。

    > [!TIP]
    > プロセスにアタッチする、正常に接続しても、必要なプロセスが表示されない場合は、選択、**プロセスすべてのユーザー チェック ボックスを表示する**です。 別のユーザー アカウントで接続しているかどうかのプロセスが表示されます。

4. 次の手順でこのエラーが解決しない場合は、次を参照してください。[リモート コンピューターに到達できません](#dns)です。

## <a name="rejected"></a>接続要求は、リモート デバッガーによって拒否されました

**プロセスにアタッチする** ダイアログ ボックスまたはプロジェクトのプロパティで、リモート コンピューター名とポート番号がリモート デバッガー ウィンドウに表示される名前とポート番号と一致していることを確認します。 正しくない場合は修正してからやり直してください。

これらの値が適切であり、メッセージを示す場合**Windows 認証**モードでは、リモート デバッガーが適切な認証モードであることを確認 (**ツール > オプション**)。

## <a name="invalid_access"></a>メモリ位置への正しくないアクセス

内部エラーが発生しました。 Visual Studio を再起動し、もう一度やり直してください。

## <a name="no_server"></a>指定された名前、リモート コンピューターで実行されているサーバーは存在しません

Visual Studio は、リモート デバッガーに接続できませんでした。 このメッセージは、いくつかの理由が発生する可能性があります。

- リモート デバッガーは、別のユーザー アカウントで実行されている可能性があります。 参照してください[手順](#user_accounts)

- ポートがファイアウォールでブロックされます。 ファイアウォールが確認[要求をブロックしていない](#firewall)サードパーティ製のファイアウォールを使用している場合に特にです。

- リモート デバッガーのバージョンでは、Visual Studio は一致しません。 リモート デバッガーの正しいバージョンを取得するには、次を参照してください[リモート デバッグ。](../debugger/remote-debugging.md)


## <a name="#valid_name"></a>要求された名前が有効では、要求された型のデータが見つかりません

リモート コンピューターが存在するが、Visual Studio はリモート デバッガーに接続できませんでした。 このメッセージは、いくつかの理由が発生する可能性があります。

- DNS の問題には、接続がブロックされます。 参照してください[手順](#dns)です。

- リモート デバッガーは、別のユーザー アカウントで実行されている可能性があります。 次の[手順](#user_accounts)です。

- ポートがファイアウォールでブロックされます。 ファイアウォールが確認[要求をブロックしていない](#firewall)サードパーティ製のファイアウォールを使用している場合に特にです。

- リモート デバッガーのバージョンでは、Visual Studio は一致しません。 リモート デバッガーの正しいバージョンを取得するには、次を参照してください。[リモート デバッグ](../debugger/remote-debugging.md)です。

## <a name="cant_connect_back"></a>ターゲット コンピューターに Visual Studio リモート デバッガーは、このコンピューターに接続できません。

リモート デバッガーは、別のユーザー アカウントで実行されている可能性があります。 リモート デバッガーで開く**ツール > のアクセス許可**リモート デバッガーのアクセス許可にユーザーを追加します。 詳細については、次を参照してください。[リモート デバッガーが別のユーザー アカウントで実行されている](#user_accounts)です。

エラー メッセージも参照している場合、ファイアウォール、ローカル コンピューター上のファイアウォールできない可能性がありますに Visual Studio に戻り、リモート コンピューターからの通信します。 参照してください[手順](#firewall)です。

## <a name="access_denied"></a>アクセスが拒否されました

(サポートされていません)、32 ビット コンピューターから 64 ビットのリモート コンピューター上でのデバッグしようとする場合は、このエラーを表示する場合があります。

## <a name="security_package"></a>セキュリティ パッケージの特定のエラーが発生しました

Windows XP および Windows 7 に固有の従来の問題があります。 これを参照してください[情報](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package)です。 

## <a name="causes-and-recommendations"></a>原因と推奨事項

### <a name="dns"></a>リモート コンピューターに到達できません。 

リモート コンピューター名を使用して接続できない場合は、代わりに IP アドレスを使用してください。 使用することができます`ipconfig`IPv4 アドレスを取得するリモート コンピューター上のコマンドラインでします。 HOSTS ファイルを使用している場合は、正しく構成されていることを確認します。

失敗した場合、リモート コンピューターがネットワークにアクセスできることを確認してください ([ping](https://technet.microsoft.com/en-us/library/cc732509(v=ws.10).aspx)リモート コンピューター)。 インターネット経由でリモート デバッグはサポートされていませんが、一部の Microsoft Azure のシナリオでは可します。
  
### <a name="server_incorrect"></a>サーバー名が正しくないか、サード パーティのソフトウェアがリモート デバッガーに干渉すること

Visual Studio でのプロジェクト プロパティを確認し、サーバー名が正しいかどうかを確認します。 トピックをご覧ください[c# および Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp)と[C++](../debugger/remote-debugging-cpp.md#remote_cplusplus)です。 ASP.NET、開く**プロパティまたは Web/サーバー**または**プロパティ/デバッグ**プロジェクトの種類によって異なります。

> [!NOTE]
> 場合は、プロセスにアタッチする、プロジェクトのプロパティでは、リモートの設定は使用されません。

サーバー名が正しい場合は、ウイルス対策ソフトウェアまたはサード パーティ製のファイアウォールがブロックされる場合、リモート デバッガーです。 をローカルでのデバッグにこれは Visual Studio には 64 ビット バージョンのリモート デバッガーを使用して 64 ビット アプリケーションをデバッグするために、32 ビット アプリケーションは発生します。 32 ビットおよび 64 ビット プロセスでは、ローカル コンピューター内のローカル ネットワークを使用してを通信します。 コンピューターからネットワーク トラフィックが送信されることはありませんが、サード パーティのセキュリティ ソフトウェアが通信を妨げる可能性があります。

### <a name="user_accounts"></a>リモート デバッガーが別のユーザー アカウントで実行されています。 

リモート デバッガーが、既定では、のみを許可、リモート デバッガーと Administrators グループのメンバーを起動したユーザーからの接続。 ユーザーを追加する必要があります明示的に付与するアクセス許可。 
 
これは、次のいずれかの方法で解消できます。  

-   Visual Studio ユーザー、リモート デバッガーのアクセス許可を追加 (リモート デバッガー ウィンドウで選択**ツール > のアクセス許可**)。

-   リモートのコンピューターで、Visual Studio コンピューター上で使用するパスワードと同じユーザー アカウントでリモート デバッガーを再起動します。

    > [!NOTE]
    > リモート サーバーでリモート デバッガーを実行している場合は、リモート デバッガー アプリケーションを右クリックして選択**管理者として実行**(または、サービスとしてリモート デバッガーを実行することができます)。 リモート サーバーで実行しているされない場合、だけ、正常に起動します。
  
-   使用してコマンドラインからリモート デバッガーを開始することができます、 **/allow\<ユーザー名 >**パラメーター:`msvsmon /allow <username@computer>`です。 
  
-   また、すべてのユーザーにリモート デバッグを許可できます。 リモート デバッガー ウィンドウに移動、**ツール > オプション**ダイアログ。 **[認証なし]**を選択すると、 **[すべてのユーザーにデバッグを許可する]**をチェックできるようになります。 ただし、その他のオプションが失敗した場合にのみ、またはプライベート ネットワーク上にいる場合は、このオプションを試してください。

### <a name="firewall"></a>リモート コンピューター上のファイアウォールがリモート デバッガーへの着信接続を許可しません  
 Visual Studio とリモート デバッガーの間の通信を許可するように、Visual Studio のコンピューター上のファイアウォールとリモート コンピューター上のファイアウォールを構成する必要があります。 リモート デバッガーが使用するポートについては、「 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)」を参照してください。 Windows ファイアウォールを構成する方法については、「 [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md)」を参照してください。
  
### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>リモート デバッガーのバージョンは Visual Studio のバージョンと一致しません  
 ローカルで実行している Visual Studio のバージョンは、リモート コンピューターで実行されているリモート デバッグ モニターのバージョンと一致している必要があります。 これを解決するには、リモート デバッグ モニターの一致するバージョンをダウンロードして、インストールします。 リモート デバッガーの正しいバージョンを取得するには、次を参照してください。[リモート デバッグ](../debugger/remote-debugging.md)です。
  
### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>ローカル コンピューターとリモート コンピューターの認証モードが異なる  
 ローカル コンピューターとリモート コンピューターで、同じ認証モードを使用する必要があります。 これを解決するには、両方のマシンで同じ認証モードを使用するようにします。 認証モードを変更することができます。 リモート デバッガー ウィンドウに移動、**ツール > オプション** ダイアログ ボックス。
  
 認証モードの詳細については、「 [Windows 認証の概要](https://technet.microsoft.com/en-us/library/hh831472.aspx)」を参照してください。   
  
### <a name="anti-virus-software-is-blocking-the-connections"></a>ウイルス対策ソフトウェアが接続をブロックしている  
 Windows のウイルス対策ソフトウェアがリモート デバッガーの接続を許可しても、その他のサード パーティ製のウイルス対策ソフトウェアがそれらの接続をブロックする可能性があります。 これらの接続を許可する方法については、ウイルス対策ソフトウェアのマニュアルを参照してください。  
  
### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>ネットワーク セキュリティ ポリシーによってリモート コンピューターと Visual Studio の間の通信がブロックされる  
 ネットワーク セキュリティを調べ、通信をブロックしていないことを確認します。 Windows ネットワーク セキュリティ ポリシーの詳細については、次を参照してください。[セキュリティ ポリシー設定](/windows/device-security/security-policy-settings/security-policy-settings)です。  
  
### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>ネットワークがビジー状態でリモート デバッグをサポートできない  
 リモート デバッグを別の時点で実行するか、ネットワークでの作業を別の時点にスケジュールし直す必要がある場合があります。  
  
## <a name="more-help"></a>その他のヘルプ  
 複数のリモート デバッガーのヘルプを表示する、リモート デバッガーのヘルプ ページを開きます (**ヘルプ > 使用状況**リモート デバッガーで)。
  
## <a name="see-also"></a>関連項目  
 [Remote Debugging](../debugger/remote-debugging.md)
