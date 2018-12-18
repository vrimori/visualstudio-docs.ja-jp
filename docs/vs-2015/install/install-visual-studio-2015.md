---
title: Visual Studio 2015 のインストール | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- Visual Studio, installing
- installing Visual Studio
- server installations [Visual Studio]
- Setup [Visual Studio]
- install Visual Studio
- visual studio installer
ms.assetid: da049020-cfda-40d7-8ff4-7492772b620f
caps.latest.revision: 183
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 761264d80c04f0e2ce13a365071f56739d6961a2
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055168"
---
# <a name="install-visual-studio-2015"></a>Visual Studio 2015 のインストール

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このページには、開発者用の生産性ツールの統合されたスイートである、**Visual Studio 2015** をインストールする際に役立つ詳細情報が含まれています。 [機能](https://www.visualstudio.com/news/vs2015-vs.aspx)、 [エディション](http://go.microsoft.com/fwlink/?LinkID=242142)、 [システム要件](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs)、 [ダウンロード](http://go.microsoft.com/fwlink/?LinkId=517106)などの情報にすばやくアクセスできるリンクも記載しています。

## <a name="quick-links"></a>クイック リンク

詳細について説明する前に、最も頻繁に要求されたリンクを列挙します。

|||
|------------------|----------------|
|![Visual Studio のダウンロード](../install/media/downloads.png "ダウンロード") |**ダウンロード**Visual Studio 2015 をインストールするには、製品の実行可能ファイルからダウンロードできます、 [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) (サブスクリプションが必要) ページ、またはボックス化された製品のインストール メディアを使用します。 [現在または以前のバージョンの Visual Studio をダウンロードする方法についての詳細は](https://www.visualstudio.com/vs/older-downloads/)します。|
|![機能の詳細について](../install/media/features.png "機能") |**機能**Visual Studio 2015 の機能に関する詳細については、リリース ノートを参照してください。 [RTM](https://www.visualstudio.com/news/vs2015-vs)、 [Update 1](https://www.visualstudio.com/news/vs2015-update1-vs)、 [Update 2](https://www.visualstudio.com/news/vs2015-update2-vs)、および[Update 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs)します。|
|![各 SKU で新機能については](../install/media/sku.png "Sku") |**SKU**:Visual Studio 2015 の各エディションに用意されている提供物については、「[Visual Studio 製品の比較](http://go.microsoft.com/fwlink/?LinkID=242142)」ページを参照してください。|
|![システム要件を表示](../install/media/system-requirements.png "システム要件") |**システム要件**:Visual Studio 2015 の各エディションのシステム要件については、「[Visual Studio 2015 の互換性](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs)」ページを参照してください。|
|![プロダクト キーを検索](../install/media/product-keys.png "プロダクト キー") |**プロダクト キー**プロダクト キーを検索するを参照してください、[方法。Visual Studio プロダクト キーを検索](../install/how-to-locate-the-visual-studio-product-key.md)トピック。|
|![ライセンスをお探し](../install/media/licensing.png "ライセンス") |**ライセンス**:個人または企業のお客様の両方のライセンス オプションについては、「[Visual Studio と MSDN のライセンス](https://www.microsoft.com/download/details.aspx?id=13350)」ホワイト ペーパーを参照してください。|

##  <a name="custom"></a> 既定値とカスタム セットアップ
 Visual Studio 2015 をインストールするときに、日常的に使用するコンポーネントを含めたり除外したりできます。 一般的に、既定のインストールはカスタム インストールよりサイズが小さく、インストールにかかる時間も短くなります。 また、以前のバージョンで既定でインストールされていたコンポーネントの多数が、このバージョンでは、明示的に選択する必要があるカスタム コンポーネントと見なされるようになりました。

 ![Visual Studio 2015 のセットアップ ダイアログ](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 カスタム コンポーネントに含まれるのは、Visual C++、Visual F#、SQL Server Data Tools、クロス プラットフォームのモバイル ツールおよび SDK、サード パーティの SDK、拡張機能などです。 カスタム コンポーネントはいずれも、初期セットアップ時に選択しなくても後でインストールすることができます。

> [!NOTE]
>  カスタム インストールには、既定のインストールに含まれるコンポーネントが自動的に組み込まれます。

 カスタム コンポーネントの完全な一覧は、次のとおりです。

|機能セット|コンポーネント|
|------------------|----------------|
|**更新**|Visual Studio 2015 更新プログラム 3|
|**プログラミング言語**|Visual C++<br />Visual F#<br />Python Tools for Visual Studio|
|**Windows 開発および Web 開発**|ClickOnce 発行ツール<br />LightSwitch<br />Microsoft Office Developer Tools<br />Microsoft SQL Server Data Tools<br /> Microsoft Web Developer Tools<br />PowerShell Tools for Visual Studio (サード パーティの)<br />Silverlight 開発キット<br />ユニバーサル Windows アプリ開発ツール<br />Windows 10 のツールおよび SDK<br />Windows 8.1 および Windows Phone 8.0/8.1 ツール<br />Windows 8.1 のツールおよび SDK|
|**クロス プラットフォームのモバイル開発**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />iOS/Android 向け Visual C++ モバイル開発<br />Clang with Microsoft CodeGen|
|**一般的なツールとソフトウェア開発キット**|Android Native Development Kit (サード パーティの)<br /> Android SDK [サード パーティ]<br />Android SDK セットアップ Api (サード パーティの)<br />Apache Ant (サード パーティの)<br /> Java SE Development Kit (サード パーティの)<br /> Joyent Node.js (サード パーティの)|
|**一般的なツール**|Git for Windows (サード パーティの)<br />Visual Studio 向け GitHub 拡張 (サード パーティの)<br /> Visual Studio 機能拡張ツール|

##  <a name="installing"></a> Visual Studio のインストール
 インストール メディア (Dvd) を使用してから、Visual Studio サブスクリプションのサービスを使用して、Visual Studio をインストールすることができます、 [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015)から web インストーラーをダウンロードすることによって、web サイト、 [Visual Studioダウンロード](http://go.microsoft.com/fwlink/?LinkId=517106)web サイト、またはオフライン インストール レイアウトを作成して (を参照してください、[の作成、オフライン インストールの Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)の詳細 ページ)。

> [!IMPORTANT]
>  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]をインストールするには、管理者の資格情報が必要です。 ただしインストール後、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] の使用には不要です。

 Visual Studio のすべてをインストールするには、ローカル管理者アカウントの次の特権が有効になっている必要があります。

|ローカル ポリシー オブジェクト表示名|ユーザー権限|
|--------------------------------------|----------------|
|ファイルとディレクトリのバックアップ|SeBackupPrivilege|
|プログラムのデバッグ|SeDebugPrivilege|
|監査ログとセキュリティ ログの管理|SeSecurityPrivilege|

 ローカル管理者アカウントの要件の詳細については、サポート技術情報「 [セットアップ アカウントに特定のユーザー権限がない場合、SQL Server のインストールが失敗する](https://support.microsoft.com/en-us/kb/2000257)」を参照してください。

###  <a name="BKMK_Media"></a> インストール メディアを使用します。
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]をインストールするには、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] インストール メディアのルート ディレクトリで、必要なエディションのインストール ファイルを実行します。

|エディション|インストール ファイル|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Visual Studio コミュニティ|vs_community.exe|

###  <a name="BKMK_Website"></a> 製品の web サイトからダウンロードします。
 参照してください、 [Visual Studio のダウンロード](http://go.microsoft.com/fwlink/?LinkId=517106)] ページの [とする Visual Studio のエディションを選択します。

### <a name="downloading-from-your-subscription-service"></a>サブスクリプションのサービスからのダウンロード
 参照してください、 [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) ] ページの [とする Visual Studio のエディションを選択します。

###  <a name="BKMK_Offline"></a> オフライン インストール レイアウトを作成します。
 ない場合、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]またはインストール メディアに、Visual Studio サブスクリプションがないかをインストールしたくない[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]web インストーラーを使用して、オフラインと呼ばれるものを作成して「切断済み」のインストールを実行することができますインストール レイアウト。 詳細については、次を参照してください。、 [、の Visual Studio オフライン インストールを作成](../install/create-an-offline-installation-of-visual-studio.md)ページ。

##  <a name="enterprise"></a> 企業での Visual Studio の展開
 デプロイする方法については[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]、ネットワーク経由で、次を参照してください。、 [Visual Studio 管理者ガイド](../install/visual-studio-administrator-guide.md)します。

###  <a name="BKMK_Virtualized"></a> 仮想化環境で Visual Studio のインストール
 **Hyper-V に関するビデオの問題**

 Hyper-V が有効であり、アクセラレータ機能を使用するグラフィックス アダプターが搭載されている Windows Server 2008 R2 を実行すると、システムの速度が低下することがあります。

 詳細については、Microsoft web サイトで、次のページを参照してください。[ビデオのパフォーマンスが低下する場合、Windows Server 2008 または Windows Server 2008 の R2 ベースのコンピューターが、HYPER-V の役割を有効にし、インストールされている高速化されたディスプレイ アダプター](http://go.microsoft.com/fwlink/?LinkID=231084)します。

 **Hyper-V によるデバイスのエミュレート**

 仮想化を使わずに Visual Studio 2015 を実際のハードウェアにインストールする場合、Hyper-V を使用して Windows デバイスと Android デバイスのエミュレーションを有効にする機能を選択できます。 HYPER-V にインストールすると、Windows デバイスまたは Android デバイスをエミュレートできなくなります。 これは、エミュレーター自体が仮想マシンであり、現時点では別の VM の内部で VM をホストすることができないためです。 回避策として、アプリケーションを直接デプロイおよびデバッグできる実際の Windows デバイスまたは Android デバイスを用意することができます。

##  <a name="optionalComponents"></a> 省略可能なコンポーネントをインストールします。
 元のインストール中に選択した可能性がありますいないコンポーネントをインストールする場合は、次の手順を使用します。

#### <a name="to-install-optional-components"></a>省略可能なコンポーネントをインストールするには

1.  **[コントロール パネル]** の **[プログラムと機能]** ページで、1 つまたは複数のコンポーネントを追加する製品のエディションを選択し、 **[変更]** を選択します。

2.  セットアップ ウィザードで、 **[変更]** を選択し、インストールするコンポーネントを選択します。

3.  **[次へ]** を選択し、残りの指示に従います。

##  <a name="helpContent"></a> オフラインのヘルプ コンテンツのインストール
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]をインストールした後、オフラインで使用できるように、追加のヘルプ コンテンツをダウンロードすることができます。

#### <a name="to-install-or-uninstall-help-content"></a>ヘルプ コンテンツをインストールまたはアンインストールするには

1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] メニュー バーで、 **[ヘルプ]**、 **[ヘルプ コンテンツの追加と削除]** の順にクリックします。

2. **[Microsoft ヘルプ ビューア―]** の **[コンテンツの管理]** タブで、ヘルプ コンテンツのインストール ソースを選択します。

3. 特定のヘルプ コレクションを検索する場合は、**[検索]** ボックスに名前やキーワードを入力し、**Enter** キーを押します。

4. 必要なヘルプ コレクションの横で、 **[追加]** または **[削除]** リンクをクリックします。

5. をクリックして、 **Update**ボタンをクリックします。

   インストールまたはオフラインのヘルプをデプロイする方法の詳細については、次を参照してください。、[ヘルプ ビューアーの管理者ガイド](../ide/help-viewer-administrator-guide.md)します。

##  <a name="serviceReleases"></a> サービス リリースと製品の更新プログラムのチェック
 すべての拡張機能に互換性があるわけではないので、以前のバージョンからアップグレードするときに、Visual Studio は拡張機能を自動的にアップグレードしません。 拡張機能を再インストールする必要があります、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkId=178891)またはソフトウェア発行者から。

#### <a name="to-automatically-check-for-service-releases"></a>サービス リリースを自動的に確認するには

1.  メニュー バーの **[ツール]**、 **[オプション]** の順にクリックします。

2.  **[オプション]** ダイアログ ボックスの **[環境]** を展開し、 **[拡張機能と更新プログラム]** をクリックします。 **[更新プログラムを自動的にチェックする]** チェック ボックスが選択されていることを確認し、 **[OK]** をクリックします。

## <a name="registering-visual-studio"></a>Visual Studio の登録

1.  メニュー バーで、 **[ヘルプ]**、 **[バージョン情報]** の順にクリックします。

     **[バージョン情報]** ダイアログ ボックスに製品 ID 番号 (PID) が表示されます。 製品を登録するには、PID と Windows アカウントの資格情報 (Hotmail や Outlook.com などの電子メール アドレスとパスワード) が必要です。

2.  メニュー バーで、 **[ヘルプ]**、 **[製品の登録]** の順に選択します。

##  <a name="repair"></a> Visual Studio の修復

#### <a name="to-repair-visual-studio"></a>Visual Studio を修復するには

1.  **[コントロール パネル]** の **[プログラムと機能]** ページで、修復する製品のエディションを選択し、 **[変更]** を選択します。

2.  セットアップ ウィザードで、 **[修復]**、 **[次へ]** の順に選択し、残りの指示に従います。

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>サイレント モードまたはパッシブ モードで Visual Studio を修復する (つまり、ソースから修復する)

1.  Visual Studio がインストールされているコンピューターで、Windows コマンド プロンプトを開きます。

2.  次のパラメーターを入力します。

     *DVDRoot* \\< インストール ファイル\> \</quiet&#124;/passive > [/norestart]/修復

##  <a name="troubleshooting"></a> インストールのトラブルシューティング
 セットアップとインストールの問題に対して次のリソースを使用します。

-   「[Visual Studio Setup and Installation (Visual Studio のセットアップとインストール)](http://go.microsoft.com/fwlink/?LinkID=151190) 」フォーラム。 Visual Studio コミュニティでは、他のユーザーからの質問と回答を閲覧できます。 必要な情報が見つからない場合は、自分で質問してください。

-   「[Microsoft Support for Visual Studio (Visual Studio 用の Microsoft サポート)](http://go.microsoft.com/fwlink/?LinkID=251019) 」Web サイト。 サポート技術情報 (KB) の文書を読むことや、Visual Studio のインストールに関する問題について Microsoft サポートに問い合わせる方法を知ることができます。

##  <a name="relatedTopics"></a> 関連トピック

|Title|説明|
|-----------|-----------------|
|[Visual Studio のオフライン インストールを作成する](../install/create-an-offline-installation-of-visual-studio.md)|インターネットに接続されていないときに、Visual Studio をインストールする方法について説明します。
|[複数バージョンの Visual Studio をインストールする](../install/install-visual-studio-versions-side-by-side.md)|同じコンピューターに複数バージョンの Visual Studio をインストールする方法について説明します。|
|[コマンド ライン パラメーターを使用して Visual Studio をインストールする](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|コマンド プロンプトから Visual Studio をインストールするときに使用できるコマンド ライン パラメーターを一覧表示します。|
|[Visual Studio のアンインストール](../install/uninstall-visual-studio.md)|Visual Studio をアンインストールする方法について説明します。|
|[Visual Studio 管理者ガイド](../install/visual-studio-administrator-guide.md)|Visual Studio の配置オプションについて説明します。|
|[Visual Studio Image Library](../designers/the-visual-studio-image-library.md)|Visual Studio アプリケーションで使用できるグラフィックスをインストールする方法について説明します。|
|[Get Started Developing with Visual Studio](../ide/get-started-developing-with-visual-studio.md)|情報と Visual Studio をより効果的に使用するのに役立つリンクが含まれています。|

## <a name="see-also"></a>参照

- [Visual Studio へのサインイン](../ide/signing-in-to-visual-studio.md)