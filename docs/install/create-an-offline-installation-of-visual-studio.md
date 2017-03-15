---
title: "Visual Studio 2017 RC のオフライン インストールを作成する | Microsoft Docs"
description: "Visual Studio のオフライン インストールを作成する方法について説明します。"
ms.custom: 
ms.date: 02/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
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
ms.sourcegitcommit: d4d1bd45ce697017480b3f63d0c7feb5ab20d2d6
ms.openlocfilehash: 33e765d205aa7ad8a3d8c5b871863ab659092a77
ms.lasthandoff: 02/22/2017

---
# <a name="create-an-offline-installation-of-visual-studio-2017-rc"></a>Visual Studio 2017 RC のオフライン インストールを作成する

## <a name="create-a-layout"></a>レイアウトを作成する
インターネットにアクセスできない別のコンピューターに [Visual Studio 2017 RC](https://www.visualstudio.com/vs/visual-studio-2017-rc/) をインストールする場合は、まず、必要な Visual Studio のファイルとコンポーネントをすべて含むオフライン インストール レイアウトを作成します。

その後、作成したオフライン インストール レイアウトを使用して、ターゲット コンピューターに Visual Studio をインストールできます。     

> [!WARNING]
> 現在、Android SDK はオフライン インストール エクスペリエンスをサポートしていません。 Android SDK セットアップ項目をインターネットに接続されていないコンピューターにインストールする場合、インストールが失敗する可能性があります。 このトピックの「[オフライン インストールのトラブルシューティング](#tshootofflineinstall)」セクションに移動して、詳細を確認してください。


#### <a name="to-create-an-offline-installation-layout-of-visual-studio"></a>Visual Studio のオフライン インストール レイアウトを作成するには
1. Visual Studio セットアップ実行可能ファイルを、ローカル コンピューター上のドライブにダウンロードします。
  たとえば、[vs_enterprise.exe ファイルをダウンロード](https://www.visualstudio.com/vs/visual-studio-2017-rc/)します。
2. コマンド プロンプトから以下の引数 (スイッチ) を指定して、`vs_enterprise.exe` を実行します。

   a.  `--layout <path>` を追加します。ここで `<path>` は、レイアウトのダウンロード先の場所です。 現時点では、相対パス (`..\vs2017` など) はサポートされていないことに注意してください。 既定では、すべての言語がダウンロードされます  (例 A を参照)。

   b.  `--lang <language>` 引数 (ここで `<language>` は&1; つ以上の言語ロケールです) を指定して、使用可能な言語のサブセットへのダウンロードを制限します   (例の B と C を参照)。

   c. `--add <package ID>` 引数を指定して、ワークロードとコンポーネントのサブセットへのダウンロードを制限します。 これで、指定したワークロードとコンポーネント (およびその依存関係) のみがダウンロードされます  (例の D と E を参照)。

   Visual Studio 製品ごとに並べられているワークロードとコンポーネント ID の完全な一覧については、[Visual Studio 2017 のワークロードとコンポーネント ID](https://aka.ms/vs2017componentids) に関するページを参照してください。

### <a name="examples"></a>例
**例 A**: すべての言語に対して、すべてのワークロードとコンポーネントをダウンロードする
  > ```vs_enterprise.exe --layout C:\vs2017```

**例 B**:&1; つの言語に対して、すべてのワークロードとコンポーネントをダウンロードする  
  > ```vs_enterprise.exe --layout C:\vs2017 --lang en-US```

**例 C**: 複数の言語に対して、すべてのワークロードとコンポーネントをダウンロードする
  > ```vs_enterprise.exe --layout C:\vs2017 --lang en-US de-DE ja-JP```

**例 D**: すべての言語に対して、1 つのワークロードをダウンロードする
  > ```vs_enterprise.exe --layout C:\vs2017 --add Microsoft.VisualStudio.Workload.Azure ```

**例 E**:&3; つの言語に対して、2 つのワークロードと&1; つのオプション コンポーネントをダウンロードする
  > ```vs_enterprise.exe --layout C:\vs2017 --add Microsoft.VisualStudio.Workload.Azure Microsoft.VisualStudio.Workload.ManagedDesktop Component.GitHub.VisualStudio --lang en-US de-DE ja-JP ```

  > [!WARNING]
  > セットアップの .exe ファイルの名前に数字が含まれていると、--layout パラメーターは失敗します。 この問題を解決するには、ファイル名から数字を削除する必要があります。&mdash;たとえば、*vs_community__198521760.1486960229.exe* という名前を ***vs_community.exe*** に変更します。

### <a name="language-locales"></a>言語ロケール

| 言語ロケール | 言語 |
| -----   | ----- |
| cs-CZ    | チェコ語 |
| de-DE    | ドイツ語 |
| en-US    | 英語 |
| es-ES    | スペイン語 |
| fr-FR    | フランス語 |
| it-IT    | イタリア語 |
| ja-JP    | 日本語 |
| ko-KR    | 韓国語 |
| pl-PL    | ポーランド語 |
| pt-BR    | ポルトガル語 - ブラジル |
| ru-RU    | ロシア語 |
| tr-TR    | トルコ語 |
| zh-CN    | 中国語 - 簡体字 |
| zh-TW    | 中国語 - 繁体字 |


## <a name="install-from-a-layout"></a>レイアウトからのインストール
#### <a name="to-install-visual-studio-from-an-offline-installation-layout"></a>オフライン インストール レイアウトから Visual Studio をインストールするには
1. ターゲット コンピューターで、レイアウト フォルダー内にある **Certificates** フォルダーに移動します。
2. **Certificates** フォルダーの各証明書を右クリックしてインストールします 

  (証明書をインストールした後でパスワードの入力を求められたら、**[続行]** をクリックします)。  
3. **レイアウト** フォルダーから `vs_enterprise.exe` を実行します。

注: 部分レイアウトからインストールする際に、レイアウトで使用できないワークロード、コンポーネントまたは言語を選択した場合、セットアップでそれらのダウンロードが試行されます。  インターネットにアクセスできない場合、それらのアイテムのインストールは失敗します。

> [!CAUTION]
> 現在、オフライン インストール レイアウトでは、すべてのユーザーがアクセスできないようにする制限されたアクセス許可 (ACL) を使用していくつかのファイルが作成されます。  オフライン インストールを共有する*前*に、他のユーザーに読み取りアクセス権を付与するように、必ずアクセス許可 (ACL) を調整してください。

## <a name="update-an-installation-layout"></a>インストール レイアウトを更新する
Visual Studio 2017 RC の更新プログラムが利用可能になった場合は、同じレイアウト フォルダーをポイントし、`--layout` コマンドを再度実行して、フォルダーに最新のコンポーネントが含まれていることを確認できます。 最後に `--layout` が実行されてから更新されたコンポーネントのみがダウンロードされます。

## <a id="tshootofflineinstall"> </a>インストール レイアウトのトラブルシューティング
オフライン インストール キャッシュからオフラインでインストールする際に、一部のコンポーネントとパッケージをインストールできないことを示す警告メッセージが表示される場合があります。 そのようなシナリオで使用可能なソリューションを以下の表に示します。

| コンポーネントまたはパッケージ | ソリューション |
| -------------------- | -------- |
|Android SDK セットアップ (API レベル)| Android SDK (API レベル) パッケージをインストールするには、インターネットに接続する必要があります。 制限付きネットワークを使用している場合は、Visual Studio のインストール時に次の URL へのアクセスを許可する必要があります。 <br><br> - http://dl.google.com:443 <br>- http://dl-ssl.google.com:443 <br>  - https://dl-ssl.google.com/android/repository/*<br><br>プロキシ設定で考えられる問題を解決する方法の詳細については、ブログ投稿の「[Visual Studio install failures (Android SDK Setup) behind a Proxy](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/)」 (プロキシ経由で Visual Studio をインストールできない (Android SDK セットアップ)) を参照してください。  |  

 > [!IMPORTANT]
 > Visual Studio 2017 RC は一般に運用環境での使用がサポートされていますが、インストール UI で "プレビュー" とマークされているワークロードやコンポーネントは運用環境での使用がサポートされていません。

 ## <a name="see-also"></a>関連項目
 * [Visual Studio のインストール](install-visual-studio.md)
 * [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
 * [Visual Studio で問題を報告する](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

