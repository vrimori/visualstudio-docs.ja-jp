---
title: "Visual Studio のインストール | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "vs.about"
helpviewer_keywords: 
  - "Visual Studio、インストール"
  - "インストール (Visual Studio の)"
  - "サーバー インストール [Visual Studio]"
  - "セットアップ [Visual Studio]"
  - "インストール (Visual Studio の)"
ms.assetid: da049020-cfda-40d7-8ff4-7492772b620f
caps.latest.revision: 177
caps.handback.revision: 150
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Visual Studio のインストール
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このページには、開発者用の生産性ツールの統合されたスイートである、Visual Studio 2015 をインストールする際に役立つ詳細情報が含まれています。[機能](https://www.visualstudio.com/en-us/news/vs2015-vs.aspx)、[エディション](http://go.microsoft.com/fwlink/?LinkID=242142)、[システム要件](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs)、[ダウンロード](http://go.microsoft.com/fwlink/?LinkId=517106)などの情報にすばやくアクセスできるリンクも記載しています。  
  
> [!TIP]
>  Visual Studio の以前のバージョンに関するインストール情報を表示するには、このページの上部にある \[その他のバージョン\] リンクをクリックします。  
  
## クイック リンク  
 詳細について説明する前に、最も頻繁に要求されたリンクを列挙します。  
  
|機能|  
|--------|  
|Visual Studio 2015 の新機能または更新された機能の詳細については、「[Visual Studio 2015 RTM](https://www.visualstudio.com/en-us/news/vs2015-vs.aspx)」および「[Visual Studio 2015 Update 1](https://www.visualstudio.com/news/vs2015-update1-vs)」を参照してください。|  
|Visual Studio 2015 の各エディションに用意されている提供物については、「[Visual Studio 製品の比較](http://go.microsoft.com/fwlink/?LinkID=242142)」ページを参照してください。|  
|Visual Studio 2015 の各エディションのシステム要件については、「[Visual Studio 2015 の互換性](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs)」ページを参照してください。|  
|Visual Studio 2015 をインストールするには、「[Visual Studio のダウンロード](http://go.microsoft.com/fwlink/?LinkId=517106)」からダウンロードするか、パッケージ版製品のインストール メディアを使用します。|  
|プロダクト キーを検索するには、「[方法: Visual Studio プロダクト キーを検索する](../install/how-to-locate-the-visual-studio-product-key.md)」のトピックを参照してください。|  
|個人または企業のお客様の両方のライセンス オプションについては、「[Visual Studio と MSDN のライセンス](https://www.microsoft.com/download/details.aspx?id=13350)」ホワイト ペーパーを参照してください。|  
  
##  <a name="custom"></a> 既定値とカスタム セットアップ  
 Visual Studio 2015 をインストールするときに、日常的に使用するコンポーネントを含めたり除外したりできます。 一般的に、既定のインストールはカスタム インストールよりサイズが小さく、インストールにかかる時間も短くなります。 また、以前のバージョンで既定でインストールされていたコンポーネントの多数が、このバージョンでは、明示的に選択する必要があるカスタム コンポーネントと見なされるようになりました。  
  
 ![Visual Studio 2015 のセットアップ ダイアログ](~/docs/ide/media/vs2015_setup_screen.png "VS2015\_Setup\_screen")  
  
 カスタム コンポーネントに含まれるのは、Visual C\+\+、Visual F\#、SQL Server Data Tools、クロス プラットフォームのモバイル ツールおよび SDK、サード パーティの SDK、拡張機能などです。 カスタム コンポーネントはいずれも、初期セットアップ時に選択しなくても後でインストールすることができます。  
  
> [!NOTE]
>  カスタム インストールには、既定のインストールに含まれるコンポーネントが自動的に組み込まれます。  
  
 カスタム コンポーネントの完全な一覧は、次のとおりです。  
  
-   **プログラミング言語**  
  
    -   Visual C\+\+ コンパイラ、ライブラリ、ツール  
  
    -   Visual F\#  
  
    -   Python Tools for Visual Studio  
  
-   **Windows 開発および Web 開発**  
  
    -   ClickOnce 発行ツール  
  
    -   Microsoft SQL Server Data Tools  
  
    -   Microsoft Web Developer Tools  
  
    -   PowerShell Tools for Visual Studio  
  
    -   Silverlight 開発キット  
  
    -   ユニバーサル Windows アプリ開発ツール  
  
    -   Windows 10 のツールおよび SDK  
  
    -   Windows 8.1 および Windows Phone 8.0\/8.1 ツール  
  
    -   Windows 8.1 のツールおよび SDK  
  
-   **クロス プラットフォームのモバイル開発**  
  
    -   Xamarin \(C\#\/.NET\)  
  
    -   Apache Cordova \(HTML\/JavaScript\)  
  
    -   iOS\/Android 向け Visual C\+\+ モバイル開発  
  
-   **一般的なツールと SDK**  
  
    -   Android Native Development Kit \(R10E、32 ビット\)  
  
    -   Android SDK  
  
    -   Android SDK セットアップ \(API レベル 19 および 21\)  
  
    -   Android SDK セットアップ \(API レベル 22\)  
  
    -   Apache Ant \(1.9.3\)  
  
    -   Java SE 開発キット \(7.0.550.13\)  
  
    -   Joyent Node.js  
  
-   **一般的なツール**  
  
    -   Git for Windows  
  
    -   Visual Studio 向け GitHub 拡張機能  
  
    -   Visual Studio 機能拡張ツール  
  
##  <a name="installing"></a> Visual Studio のインストール  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] をインストールするには、管理者の資格情報が必要です。 ただしインストール後、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の使用には不要です。  
  
 Visual Studio のすべてをインストールするには、ローカル管理者アカウントの次の特権が有効になっている必要があります。  
  
|ローカル ポリシー オブジェクト表示名|ユーザー権限|  
|-------------------------|------------|  
|ファイルとディレクトリのバックアップ|SeBackupPrivilege|  
|プログラムのデバッグ|SeDebugPrivilege|  
|監査ログとセキュリティ ログの管理|SeSecurityPrivilege|  
  
 ローカル管理者アカウントの要件の詳細については、サポート技術情報「[セットアップ アカウントに特定のユーザー権限がない場合、SQL Server のインストールが失敗する](https://support.microsoft.com/en-us/kb/2000257)」を参照してください。  
  
###  <a name="BKMK_Media"></a> インストール メディアを使用したインストール  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] をインストールするには、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] インストール メディアのルート ディレクトリで、必要なエディションのインストール ファイルを実行します。  
  
    |エディション|インストール ファイル|  
    |------------|-----------------|  
    |Visual Studio Enterprise|vs\_enterprise.exe|  
    |Visual Studio Professional|vs\_professional.exe|  
    |Visual Studio コミュニティ|vs\_community.exe|  
  
###  <a name="BKMK_Website"></a> 製品の Web サイトからのダウンロードによるインストール  
  
-   VisualStudio.com Web サイトの「[Visual Studio のダウンロード](http://go.microsoft.com/fwlink/?LinkId=517106)」にアクセスします。  
  
###  <a name="BKMK_Offline"></a> オフライン インストール用の Visual Studio のダウンロード  
 ほとんどの場合、Visual Studio をダウンロード サイトから問題なくインストールできます。 ただし、場合によっては \(複数のコンピューターまたはオフライン コンピューターにインストールする場合など\)、インストールを開始する前にすべての更新パッケージをダウンロードすることもできます。 次に示す手順では、オフライン インストールで必要とされるすべての更新パッケージをダウンロードする方法を説明します。  
  
1.  更新パッケージの実行可能ファイルを MSDN Web サイトからファイル システム内のいずれかの場所にダウンロードした後、コマンド プロンプトで `<executable name> /layout` コマンドを実行します。  
  
     このコマンドは、インストールに使用するすべてのパッケージをダウンロードします。  
  
     `/layout` スイッチを使用すると、ダウンロード先のコンピューターに適用されるコア インストール パッケージだけではなく、ほとんどすべてのコア インストール パッケージをダウンロードできます。 この方法では、任意の場所でこの更新を実行するために必要なすべてのファイルを入手できます。当初インストールしていなかったコンポーネントをインストールする場合に便利です。  
  
2.  コマンドの実行後、ダウンロード場所の入力を求められます。 場所を入力し、**\[ダウンロード\]** をクリックします。  
  
3.  パッケージのダウンロードが成功すると、Visual Studio の画面に次のメッセージが表示されます。**セットアップが正常に完了しました。指定したコンポーネントがすべて正常に取得されました。**  
  
4.  指定したファイルの場所で、実行可能ファイルとパッケージ フォルダーを見つけます。 これらすべてを、共有の場所またはインストール メディアにコピーする必要があります。  
  
    > [!CAUTION]
    >  現在、Android SDK はオフライン インストール エクスペリエンスをサポートしていません。 Android SDK セットアップ項目をインターネットに接続されていないコンピューターにインストールする場合、インストールが失敗する可能性があります。  
  
5.  これで、ファイルの場所、またはインストール メディアからインストールを実行できます。  
  
###  <a name="BKMK_Virtualized"></a> 仮想化環境での Visual Studio のインストール  
 **Hyper\-V に関するビデオの問題**  
  
 Hyper\-V が有効であり、アクセラレータ機能を使用するグラフィックス アダプターが搭載されている Windows Server 2008 R2 を実行すると、システムの速度が低下することがあります。  
  
 詳細については、Microsoft Web サイトの「[Video performance may decrease when a Windows Server 2008 or Windows Server 2008 R2 based computer has the Hyper\-V role enabled and an accelerated display adapter installed \(Windows Server 2008 または Windows Server 2008 R2 ベースのコンピューターで Hyper\-V の役割を有効にし、アクセラレータ機能を使用するディスプレイ アダプターをインストールしたときに、ビデオ パフォーマンスが低下する場合がある\)](http://go.microsoft.com/fwlink/?LinkID=231084)」を参照してください。  
  
 **Hyper\-V によるデバイスのエミュレート**  
  
 仮想化を使わずに Visual Studio 2015 を実際のハードウェアにインストールする場合、Hyper\-V を使用して Windows デバイスと Android デバイスのエミュレーションを有効にする機能を選択できます。 HYPER\-V にインストールすると、Windows デバイスまたは Android デバイスをエミュレートできなくなります。 これは、エミュレーター自体が仮想マシンであり、現時点では別の VM の内部で VM をホストすることができないためです。 回避策として、アプリケーションを直接デプロイおよびデバッグできる実際の Windows デバイスまたは Android デバイスを用意することができます。  
  
## コマンド ライン パラメーターの使用  
 インストール アプリケーションを実行するときに、次のコマンド ライン パラメーターを使用できますが、これらでは大文字と小文字が区別されます。  
  
|パラメーター|説明|  
|------------|--------|  
|**\/?**<br /><br /> **\/help**<br /><br /> **\/h**|コマンド ライン パラメーターを表示します。|  
|**\/AddRemoveFeatures**|インストールされている製品に追加または削除する機能を指定します。|  
|**\/AdminFile** *AdminDeployment.xml*|管理用インストールに指定したデータ ファイルを使用して Visual Studio をインストールします。|  
|**\/CEIPConsent**|製品プライバシー ポリシーに従って顧客の操作性を向上するための情報の収集に同意します。|  
|**\/ChainingPackage** *BundleName*|このバンドルをチェーンするバンドルを指定します。 カスタマー エクスペリエンス向上コホートの指定にも使用できます。|  
|**\/CreateAdminFile \<filename\>**|\/AdminFile と組み合わせて使用できるコントロール ファイルを作成する場所を指定します。|  
|**\/CustomInstallPath** *InstallationDirectory*|指定したディレクトリに再ターゲット可能パッケージをすべてインストールします。|  
|**\/ForceRestart**|インストール後に必ずコンピューターを再起動します。|  
|**\/full**|すべての製品の機能をインストールします。|  
|**\/InstallSelectableItems \<item name 1\>\[;\<item name 2\>\]**|インストーラー ウィザードの選択画面でチェックする選択ツリー項目の一覧。|  
|**\/l**<br /><br /> **\/Log** *Filename*|ログ ファイルの場所を指定します。|  
|**\/layout** *Directory*|インストール メディアのファイルを指定したディレクトリにコピーします。|  
|**\/NoCacheOnlyMode**|パッケージ キャッシュの事前設定を防ぎます。|  
|**\/NoRefresh**|必須の更新バージョンまたは推奨の更新バージョンに関して、この製品の新しいバージョンをチェックしないようにします。|  
|**\/norestart**|インストール中またはインストール後に、インストール アプリケーションによりコンピューターが再起動されないようにします。 検索するリターン コードについては、「[Visual Studio 管理者ガイド](../install/visual-studio-administrator-guide.md)」のリターン コードのセクションを参照してください。|  
|**\/noweb**|インターネットからインストールされないようにします。|  
|**\/OverrideFeedUri \<path to feed file\>**|ローカルへのパス。ソフトウェア項目を説明する外部フィード。|  
|**\/ProductKey**<br /><br /> *ProductKey*|ダッシュと 25 を超える文字を含まないカスタム プロダクト キーを設定します。|  
|**\/PromptRestart**|コンピューターを再起動する前にユーザーに確認します。|  
|**\/q**<br /><br /> **\/quiet**<br /><br /> **\/s**<br /><br /> **\/silent**|インストール アプリケーションのユーザー インターフェイス \(UI\) を非表示にします。 Visual Studio が既にインストールされている場合に、このパラメーター以外のパラメーターを指定しないと、インストール アプリケーションはメンテナンス モードで実行されます。|  
|**\/qb**<br /><br /> **\/passive**|進行状況が表示されますが、ユーザーの入力を待ちません。|  
|**\/repair**|Visual Studio を修復します。|  
|**\/SuppressRefreshPrompt**|インストール ウィザードに更新プログラムの入手可能ダイアログが表示されないようにし、必須の更新バージョンまたは推奨の更新バージョンが存在する場合に、インストール ウィザードで自動的に受け入れられるようにします。|  
|**\/u**<br /><br /> **\/Uninstall**|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] をアンインストールします。|  
|**\/Uninstall \/Force**<br /><br /> **\/u \/force**|Visual Studio および他の製品と共有するすべての機能をアンインストールします。 **Warning:**  このパラメーターを使用すると、同じコンピューターにインストールされている他の製品が正しく機能しなくなることがあります。|  
  
 コマンドラインからセットアップを実行するときに、コマンド ラインの操作性を改善するために、リターン コードを収集して処理することもできます。  詳細については、「[Visual Studio 管理者ガイド](../install/visual-studio-administrator-guide.md)」を参照してください。  
  
##  <a name="troubleshooting"></a> インストールのトラブルシューティング  
 セットアップとインストールの問題に対して次のリソースを使用します。  
  
-   「[Visual Studio Setup and Installation \(Visual Studio のセットアップとインストール\)](http://go.microsoft.com/fwlink/?LinkID=151190)」フォーラム。 Visual Studio コミュニティでは、他のユーザーからの質問と回答を閲覧できます。 必要な情報が見つからない場合は、自分で質問してください。  
  
-   「[Microsoft Support for Visual Studio \(Visual Studio 用の Microsoft サポート\)](http://go.microsoft.com/fwlink/?LinkID=251019)」Web サイト。 サポート技術情報 \(KB\) の文書を読むことや、Visual Studio のインストールに関する問題について Microsoft サポートに問い合わせる方法を知ることができます。  
  
-   Visual Studio 2015 のリリース版については、[https:\/\/connect.microsoft.com\/visualstudio](https://connect.microsoft.com/visualstudio) の Connect サイトを使用して、問題を報告することができます。  
  
     問題にインストール ログが含まれていればベストです。 次の手順で説明するように、Microsoft Visual Studio と .NET Framework ログ収集ツールを使用して、問題レポートのログを準備できます。  
  
    1.  インストール診断ツールは、[http:\/\/aka.ms\/vscollect](http://aka.ms/vscollect) からダウンロードします。  
  
    2.  昇格されたコマンド プロンプトから、collect.exe プログラムを実行します。  
  
    3.  collect.exe プログラムが完了した後、vslogs.cab ファイルを Temp ディレクトリから取得し、そのファイルを問題レポートにアップロードします。  
  
##  <a name="enterprise"></a> 企業内ネットワーク配置  
 ネットワーク経由で [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を配置する方法については、「[Visual Studio 管理者ガイド](../install/visual-studio-administrator-guide.md)」を参照してください。  
  
##  <a name="afterInstalling"></a> Visual Studio のインストール後の作業  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] をインストールした後、その製品を登録することをお勧めします。  
  
###  <a name="register"></a> Visual Studio の登録  
  
##### Visual Studio を登録するには  
  
1.  メニュー バーで、**\[ヘルプ\]**、**\[バージョン情報\]** の順にクリックします。  
  
     **\[バージョン情報\]** ダイアログ ボックスに製品 ID 番号 \(PID\) が表示されます。 製品を登録するには、PID と Windows アカウントの資格情報 \(Hotmail や Outlook.com などの電子メール アドレスとパスワード\) が必要です。  
  
2.  メニュー バーで、**\[ヘルプ\]**、**\[製品の登録\]** の順に選択します。  
  
###  <a name="helpContent"></a> オフラインのヘルプ コンテンツのインストール  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] をインストールした後、オフラインで使用できるように、追加のヘルプ コンテンツをダウンロードすることができます。  
  
##### ヘルプ コンテンツをインストールまたはアンインストールするには  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] メニュー バーで、**\[ヘルプ\]**、**\[ヘルプ コンテンツの追加と削除\]** の順にクリックします。  
  
2.  **\[Microsoft ヘルプ ビューア―\]** の **\[コンテンツの管理\]** タブで、ヘルプ コンテンツのインストール ソースを選択します。  
  
3.  特定のヘルプ コレクションを検索する場合は、**\[検索\]** ボックスに名前やキーワードを入力し、Enter キーを押します。  
  
4.  必要なヘルプ コレクションの横で、**\[追加\]** または **\[削除\]** リンクをクリックします。  
  
5.  **\[更新\]** をクリックします。  
  
 オフライン ヘルプの詳細については、「[Microsoft ヘルプ ビューアー 2.2 ヘルプ](../ide/microsoft-help-viewer.md)」を参照してください。  
  
###  <a name="repair"></a> Visual Studio の修復  
  
##### Visual Studio を修復するには  
  
1.  **\[コントロール パネル\]** の **\[プログラムと機能\]** ページで、修復する製品のエディションを選択し、**\[変更\]** を選択します。  
  
2.  セットアップ ウィザードで、**\[修復\]**、**\[次へ\]** の順に選択し、残りの指示に従います。  
  
##### サイレント モードまたはパッシブ モードで Visual Studio を修正する \(つまり、ソースから修復する\) には  
  
1.  Visual Studio がインストールされているコンピューターで、Windows コマンド プロンプトを開きます。  
  
2.  次のパラメーターを入力します。  
  
     *DVDRoot* \\\<Installation File\> \<\/quiet&#124;\/passive\> \[\/norestart\]\/Repair  
  
###  <a name="optionalComponents"></a> 選択可能な項目のインストール  
  
##### 選択可能な項目をインストールするには  
  
1.  **\[コントロール パネル\]** の **\[プログラムと機能\]** ページで、1 つまたは複数のコンポーネントを追加する製品のエディションを選択し、**\[変更\]** を選択します。  
  
2.  セットアップ ウィザードで、**\[変更\]** を選択し、インストールするコンポーネントを選択します。  
  
3.  **\[次へ\]** を選択し、残りの指示に従います。  
  
###  <a name="serviceReleases"></a> サービス リリースと製品の更新プログラムのチェック  
 すべての拡張機能に互換性があるわけではないので、以前のバージョンからアップグレードするときに、Visual Studio は拡張機能を自動的にアップグレードしません。[Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkId=178891)またはソフトウェア発行者から入手した拡張機能を再インストールする必要があります。  
  
##### サービス リリースを自動的に確認するには  
  
1.  メニュー バーの **\[ツール\]**、**\[オプション\]** の順にクリックします。  
  
2.  **\[オプション\]** ダイアログ ボックスの **\[環境\]** を展開し、**\[拡張機能と更新プログラム\]** をクリックします。**\[更新プログラムを自動的にチェックする\]** チェック ボックスが選択されていることを確認し、**\[OK\]** をクリックします。  
  
##  <a name="uninstalling"></a> Visual Studio のアンインストール  
 Visual Studio 2015 をアンインストールするには、次の手順に従います。  
  
#### Visual Studio をアンインストールするには  
  
1.  **\[コントロール パネル\]** の **\[プログラムと機能\]** ページで、アンインストールする製品のエディションを選択し、**\[変更\]** を選択します。  
  
2.  セットアップ ウィザードで、**\[アンインストール\]**、**\[はい\]** の順に選択し、ウィザードの残りの指示に従います。  
  
#### サイレント モードまたはパッシブ モードで Visual Studio をアンインストールする \(つまり、ソースからアンインストールする\) には  
  
1.  Visual Studio がインストールされているコンピューターで、Windows コマンド プロンプトを開きます。  
  
2.  次のパラメーターを入力します。  
  
     *DVDRoot* \\\<Installation File\> \<\/quiet&#124;\/passive\> \[\/norestart\]\/uninstall  
  
 アンインストール ユーティリティを使用しても [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] をアンインストールできない場合は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を削除してから関連するコンポーネントを削除することで、手動でアンインストールできます。 詳細については、Microsoft サポート技術情報の記事「[方法 : Visual Studio をアンインストールする](https://support.microsoft.com/en-us/kb/2771441)」、または Microsoft Server & Tools Blogs Web サイトの「[Removing Visual Studio components left behind after an uninstall \(アンインストール後に残された Visual Studio コンポーネントの削除\)](http://blogs.msdn.com/b/heaths/archive/2015/07/17/removing-visual-studio-components-left-behind-after-an-uninstall.aspx)」を参照してください。  
  
##  <a name="relatedTopics"></a> 関連トピック  
  
|タイトル|説明|  
|----------|--------|  
|[複数バージョンの Visual Studio のインストール](../Topic/Installing%20Visual%20Studio%20Versions%20Side-by-Side.md)|同じコンピューターに複数バージョンの Visual Studio をインストールする方法について説明します。|  
|[Visual Studio Image Library](../designers/the-visual-studio-image-library.md)|Visual Studio アプリケーションで使用できるグラフィックスをインストールする方法について説明します。|  
|[Visual Studio 管理者ガイド](../install/visual-studio-administrator-guide.md)|Visual Studio の配置オプションについて説明します。|  
|[複数言語バージョンの Visual Studio のインストール](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)|別の言語バージョンの Visual Studio をインストールする方法について説明します。|  
|[方法: Visual Studio プロダクト キーを検索する](../install/how-to-locate-the-visual-studio-product-key.md)|インストールしている Visual Studio のプロダクト キーを調べる方法について説明します。|  
|[作業の開始](../ide/get-started-developing-with-visual-studio.md)|Visual Studio を効果的に使用する方法を説明するドキュメントへのリンクです。|  
  
## 参照  
 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)