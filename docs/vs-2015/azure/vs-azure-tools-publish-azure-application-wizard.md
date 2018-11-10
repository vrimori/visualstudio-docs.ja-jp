---
title: Visual Studio を使用して Azure アプリケーション発行ウィザード |Microsoft Docs
description: Visual Studio の発行の Azure のアプリケーション ウィザードで、さまざまな設定を構成する方法について説明します
author: ghogen
manager: douge
assetId: 7d8f1ac9-e439-47e0-a183-0642c4ea1920
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: c9c4104d4d07cab7486038a8787ed0c7759abd60
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002969"
---
# <a name="using-the-visual-studio-publish-azure-application-wizard"></a>Visual Studio の Azure アプリケーションの公開ウィザードの使用

使用してそのアプリケーションを Azure クラウド サービスを発行するには Visual Studio で web アプリケーションを開発した後、 **Azure アプリケーションの発行**ウィザード。

> [!Note]
> この記事ではなくクラウド サービス、web サイトに展開する方法です。 Web サイトへのデプロイについては、次を参照してください。 [Azure の Web サイトをデプロイする方法](https://social.msdn.microsoft.com/Search/windowsazure?query=How%20to%20Deploy%20an%20Azure%20Web%20Site&Refinement=138&ac=4#refinementChanges=117&pageNumber=1&showMore=false)します。

## <a name="accessing-the-publish-azure-application-wizard"></a>Azure アプリケーションの発行ウィザードへのアクセス

Visual Studio プロジェクトの種類に応じて 2 つの方法で Azure アプリケーション発行ウィザードにアクセスすることができます。

**Azure クラウド サービス プロジェクトを場合。**

1. 作成または Visual Studio で Azure クラウド サービス プロジェクトを開きます。

1. **ソリューション エクスプ ローラー**プロジェクトを右クリックし、コンテキスト メニューから選択、**発行**します。

**Azure を有効になっていない web アプリケーション プロジェクトを場合。**

1. 作成または Visual Studio で Azure クラウド サービス プロジェクトを開きます。

1. **ソリューション エクスプ ローラー**プロジェクトを右クリックし、コンテキスト メニューから選択、**変換** > **Azure クラウド サービス プロジェクトに変換**します。 

1. **ソリューション エクスプ ローラー**、新しく作成した Azure プロジェクトを右クリックし、コンテキスト メニューから選択、**発行**します。

## <a name="sign-in-page"></a>サインイン ページ

![サインイン ページ](./media/vs-azure-tools-publish-azure-application-wizard/sign-in.png)

**アカウント**- アカウントを選択するか選択**アカウントを追加**アカウントのドロップダウン リスト。

**サブスクリプションの選択**-展開に使用するサブスクリプションを選択します。

## <a name="settings-page---common-settings-tab"></a>設定ページ - [共通設定] タブ

![一般的な設定](./media/vs-azure-tools-publish-azure-application-wizard/settings-common-settings.png)

**クラウド サービス**-既存のクラウド サービス、または選択を選択するか、ドロップダウン リストを使用して、 **&lt;新規作成 >**、クラウド サービスを作成します。 データ センターをクラウド サービスごとのかっこ内に表示します。 あるデータ センターの場所、クラウド サービスのストレージ アカウント (詳細設定) のデータ センターの場所と同じであることをお勧めします。

**環境**-いずれかを選択**運用**または**ステージング**します。 テスト環境でアプリケーションを展開する場合は、ステージング環境を選択します。 

**ビルド構成**-いずれかを選択**デバッグ**または**リリース**します。

**サービス構成**-いずれかを選択**クラウド**または**ローカル**します。

**すべてのロールのリモート デスクトップを有効にする**-リモート サービスに接続する場合は、このオプションを選択します。 このオプションは主のトラブルシューティングに使用します。 詳細については、次を参照してください。 [Visual Studio を使用して Azure Cloud services ロールのリモート デスクトップ接続を有効にする](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio)します。

**すべての web ロール、Web Deploy を有効に**-サービスの web 配置を有効にするには、このオプションを選択します。 選択することも必要があります、**すべてのロールのリモート デスクトップを有効にする**この機能を使用するオプション。 詳細については、次を参照してください。 [Visual Studio を使用してクラウド サービスの発行](vs-azure-tools-publishing-a-cloud-service.md)します。

## <a name="settings-page---advanced-settings-tab"></a>設定ページ - [詳細設定] タブ

![詳細設定](./media/vs-azure-tools-publish-azure-application-wizard/settings-advanced-settings.png)

**デプロイ ラベル**-既定の名前を受け入れるか、独自の名前を入力します。 デプロイ ラベルに日付を追加するには、チェック ボックスをオンのままにします。 

**ストレージ アカウント**-この展開に使用するストレージ アカウントを選択します。 * *&lt;新規作成 > ストレージ アカウントを作成します。 各ストレージ アカウントのかっこ内のデータ センターを表示します。 ストレージ アカウントのデータ センターの場所は、クラウド サービス (一般的な設定) のデータ センターの場所と同じことをお勧めします。

Azure ストレージ アカウントは、アプリケーション展開のパッケージを格納します。 アプリケーションが配置されると、パッケージは、ストレージ アカウントから削除されます。

**配置エラーを削除**-発行中にエラーが発生した場合、削除、展開するには、このオプションを選択します。 これをオフにするクラウド サービスの固定仮想 IP アドレスを保持したい場合。

**配置の更新**-更新されたコンポーネントのみを展開する場合は、このオプションを選択します。 この種類の展開は、完全なデプロイよりも高速化することはできます。 これは、クラウド サービスの固定仮想 IP アドレスを保持したい場合にチェックする必要があります。 

**配置の更新 - 設定**-このダイアログ ボックスを使用して、さらに、ロールの更新する方法を指定します。 選択した場合**増分更新**アプリケーションの各インスタンスが更新された 1 つずつ、アプリケーションが常に使用できるようにします。 選択した場合**同時更新**アプリケーションのすべてのインスタンスが同時に更新されます。 同時更新時間は短くなりますが、サービスが更新プロセス中には利用できません。

![展開の設定](./media/vs-azure-tools-publish-azure-application-wizard/deployment-settings.png)

**IntelliTrace を有効にする**-IntelliTrace を有効にするかを指定します。 Azure で実行時に、IntelliTrace を使用したロール インスタンスの広範なデバッグ情報を記録できます。 問題の原因を見つける必要がある場合は、Azure で実行されている場合に、Visual Studio からコードをステップに IntelliTrace ログを使用できます。 IntelliTrace の使用に関する詳細については、次を参照してください。[発行済みの Azure クラウド サービスに Visual Studio と IntelliTrace のデバッグ](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)します。

**プロファイリングを有効にする**-パフォーマンスのプロファイリングを有効にするかどうかを指定します。 Visual Studio プロファイラーでは、計算的側面からクラウド サービスの実行方法の詳細な分析を取得することができます。 Visual Studio プロファイラーの使用に関する詳細については、次を参照してください。 [Azure クラウド サービスのパフォーマンスをテスト](./vs-azure-tools-performance-profiling-cloud-services.md)します。

**すべてのロールのリモート デバッガーを有効にする**-リモート デバッグを有効にするかどうかを指定します。 Visual Studio を使用して cloud services のデバッグの詳細については、次を参照してください。 [Azure クラウド サービスまたは Visual Studio での仮想マシンのデバッグ](./vs-azure-tools-debug-cloud-services-virtual-machines.md)します。

## <a name="diagnostics-settings-page"></a>診断設定 ページ

![診断設定](./media/vs-azure-tools-publish-azure-application-wizard/diagnostic-settings.png)

診断を使用すると、Azure クラウド サービス (または Azure 仮想マシン) のトラブルシューティングを行うことができます。 診断についての詳細については、次を参照してください。 [Azure Cloud Services および Virtual Machines 向けの診断の構成](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md)します。 Application Insights の詳細については、次を参照してください。 [Application Insights とは何ですか?](/azure/application-insights/app-insights-overview.md)します。

## <a name="summary-page"></a>[概要] ページ

![まとめ](./media/vs-azure-tools-publish-azure-application-wizard/summary.png)

**ターゲット プロファイル**-選択した設定から発行プロファイルを作成することもできます。 たとえば、テスト環境用の 1 つのプロファイルと運用環境用に別を作成する場合があります。 このプロファイルを保存する、**保存**アイコン。 ウィザードでは、プロファイルが作成され、Visual Studio プロジェクトに保存します。 プロファイル名を変更するには、開く、**ターゲット プロファイル**一覧を選び、 **&lt;管理しています.&gt;**.

   > [!Note]
   > 発行プロファイルが Visual Studio で、ソリューション エクスプ ローラーに表示され、プロファイルの設定が .azurePubxml 拡張子を持つファイルに書き込まれます。 設定は、XML タグの属性として保存されます。

## <a name="publishing-your-application"></a>アプリケーションの発行

プロジェクトの配置のすべての設定を構成すると選択**発行**ダイアログの下部にあります。 プロセスの状態を監視することができます、**出力**Visual Studio のウィンドウ。

## <a name="next-steps"></a>次の手順

- [Visual Studio から Azure クラウド サービスに Web アプリケーション移行および発行](./vs-azure-tools-migrate-publish-web-app-to-cloud-service.md)

- [Visual Studio を使用して、Azure クラウド サービスを公開する方法について説明します](./vs-azure-tools-publishing-a-cloud-service.md)

- [発行済みの Azure クラウド サービスに Visual Studio と IntelliTrace のデバッグ](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)

- [Azure クラウド サービスのパフォーマンスをテストします。](./vs-azure-tools-performance-profiling-cloud-services.md)

- [Azure Cloud Services および Virtual Machines の診断の構成](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md)します。

- [Application Insights とは何ですか。](/azure/application-insights/app-insights-overview.md)