---
title: "Visual Studio 2017 のオフライン インストーラーを作成する | Microsoft Docs"
description: "Visual Studio のオフライン インストーラーを作成する方法について説明します。"
ms.custom: 
ms.date: 03/07/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- offline installer [Visual Studio]
- ISO [Visual Studio]
ms.assetid: 7bd7e724-7bfd-43f1-9935-981919be5a00
author: TerryGLee
ms.author: tglee
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
translationtype: Human Translation
ms.sourcegitcommit: 91fde66abf2f325ef0a6a0a2fd30e36981f44033
ms.openlocfilehash: acb47946c29d99cb53b34d67fe8a26f5611307f9
ms.lasthandoff: 03/08/2017

---
# <a name="create-an-offline-installer-for-visual-studio-2017"></a>Visual Studio 2017 のオフライン インストーラーを作成する
マイクロソフトでは、非常に多くのお客様が [Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=844067) のオフライン インストーラーを必要としていることを把握しています。 ISO イメージの提供は行っていませんが、オフライン時のインストールに使用できるフォルダーを簡単に作成することができます。

ここではその方法を説明します。

## <a name="download-the-setup-file-you-want"></a>必要なセットアップ ファイルをダウンロードする
必要な Visual Studio のエディションを**[ダウンロード](https://www.visualstudio.com/downloads?utm_source=mscom&utm_campaign=msdocs)**します。 必ず **[保存]** をクリックし、**[フォルダーを開く]** をクリックします。

セットアップ ファイル&mdash; (具体的にはブートストラップ ファイル)&mdash; は、次のいずれかになります。

|エディション | ファイル|  
|-------------|-----------------------|  
|Visual Studio Enterprise |**vs_enterprise.exe**|  
|Visual Studio Professional |**vs_professional.exe**|  
|Visual Studio コミュニティ |**vs_community.exe**|

## <a name="create-an-offline-installation-folder"></a>オフライン インストール フォルダーを作成する
すべての言語およびすべての機能を持つオフライン インストールを作成するには、次の例のいずれかのコマンドを使用します。

(コマンドをダウンロード ディレクトリから実行していることを確認してください。 通常は、Windows 10 を実行するコンピューター上の `C:\Users\<username>\Downloads` です。)

- Visual Studio Enterprise の場合、以下を実行します。 <br>  ```vs_enterprise.exe --layout c:\vs2017offline```
- Visual Studio Professional の場合、以下を実行します。 <br> ```vs_professional.exe --layout c:\vs2017offline```
- Visual Studio コミュニティの場合、以下を実行します。 <br> ```vs_community.exe --layout c:\vs2017offline```

その他の例については、このページの「[オフライン インストーラーをカスタマイズする方法](#how-to-customize-your-offline- installer)」を参照してください。

## <a name="install-from-the-offline-installation-folder"></a>オフライン インストール フォルダーからのインストール
オフライン インストールを今すぐ実行するか、後で実行するかを選択できます。 ただし、この場合、次の手順に従います。

  1. 証明書をインストールします (これらはレイアウト フォルダーの証明書フォルダーにあります。 インストールするには、それぞれを単に右クリックします)。

  2. インストール ファイルを実行します。 たとえば、以下を実行します。 <br> ```c:\vs2017offline\vs_enterprise.exe```

## <a name="additional-tips-for-offline-installers"></a>オフライン インストーラーに関するその他のヒント
オフライン インストーラーは簡単にカスタマイズまたは更新できます。その方法を以下に紹介します。 また、オフライン インストーラーで問題が生じた場合に備え、トラブルシューティングやサポート情報も用意されています。

### <a name="how-to-customize-your-offline-installer"></a>オフライン インストーラーをカスタマイズする方法
オフライン インストーラーのカスタマイズに使用できるオプションは多数あります。 これを[言語ロケール](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)別にカスタマイズする方法の例を次にいくつか紹介します。

 - 1 つの言語に対して、すべてのワークロードとコンポーネントをダウンロードするには、以下を実行します。 <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US```
 - 複数の言語に対して、すべてのワークロードとコンポーネントをダウンロードするには、以下を実行します。 <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP```
 - すべての言語に対して、1 つのワークロードをダウンロードするには、以下を実行します。 <br> ```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure ```
 - 3 つの言語に対して、2 つのワークロードと&1; つのオプション コンポーネントをダウンロードするには、以下を実行します。 <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure Microsoft.VisualStudio.Workload.ManagedDesktop Component.GitHub.VisualStudio --lang en-US de-DE ja-JP ```インストールのカスタマイズに使用できるオプションについて詳しくは、「[コマンド ライン パラメーターを使用して Visual Studio 2017 をインストールする](use-command-line-parameters-to-install-visual-studio.md)」をご覧ください。


### <a name="how-to-update-an-offline-installer"></a>オフライン インストーラーを更新する方法
オフライン インストーラーを後で更新することもできます。 ここではその方法を説明します。
* オフライン インストール フォルダーからインストールした Visual Studio インスタンスを更新するには、Visual Studio インストーラーを実行し、**[更新]** をクリックします。
* 最新の更新プログラムが含まれるようにオフライン インストール フォルダーを更新するには、もう一度 ```--layout``` コマンドを実行します。 前に使用したのと同じフォルダーをポイントしていることを確認します。これにより、最後に ```--layout``` を実行してから更新されたコンポーネントのみがダウンロードされます。


オフライン インストールを更新する場合は、もう一度 `--layout` コマンドを実行します。 前に使用したのと同じフォルダーをポイントしていることを確認します。これにより、最後に `--layout` を実行してから更新されたコンポーネントのみがダウンロードされます。

### <a name="how-to-troubleshoot-an-offline-installer"></a>オフライン インストーラーをトラブルシューティングする方法
問題が発生した場合に備え、 次に既知の問題と、便利な回避策をいくつか紹介します。

| 問題       | アイテム                   | ソリューション |
| ----------- | ---------------------- | -------- |
| 一部のコンポーネントとパッケージをインストールできないという警告メッセージが表示される。  | Android SDK セットアップ (API レベル) | Android SDK (API レベル) パッケージを含める場合、オフライン インストーラーの作成時にインターネットに接続している必要があります。 制限付きネットワークを使用している場合は、次の URL へのアクセスを許可する必要があります。 <br><br> - http://dl.google.com:443 <br> - http://dl-ssl.google.com:443 <br>  - https://dl-ssl.google.com/android/repository/*<br><br>プロキシ設定で考えられる問題を解決する方法の詳細については、ブログ投稿の「[Visual Studio install failures (Android SDK Setup) behind a Proxy](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/)」 (プロキシ経由で Visual Studio をインストールできない (Android SDK セットアップ)) を参照してください。  |  
| ユーザーにファイルへのアクセス権がない。 | アクセス許可 (ACL) | オフライン インストールを共有する*前*に、他のユーザーに読み取りアクセス権を付与するように、必ずアクセス許可 (ACL) を調整してください。 |
| 新しいワークロード、コンポーネント、または言語をインストールできない。  | `--layout`  | 部分レイアウトからインストールし、以前のレイアウトで使用できないワークロード、コンポーネント、または言語を選択した場合、インターネットにアクセスできることを確認してください。 |

### <a name="how-to-get-support-for-your-offline-installer"></a>オフライン インストーラーのサポートを受ける方法
オフライン インストールに問題が発生した場合は、マイクロソフトにお知らせください。 問題報告の最善の方法として、[[問題を報告する]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールを使用できます。 このツールでは、テレメトリとログを送信できます。これを、マイクロソフトは問題の診断と解決に役立てます。

他にも利用可能なサポート オプションがあります。 これらの一覧については、[[ご意見]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ページをご覧ください。


## <a name="see-also"></a>関連項目
* [Visual Studio のインストール](install-visual-studio.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio のワークロードとコンポーネント ID](workload-and-component-ids.md)

