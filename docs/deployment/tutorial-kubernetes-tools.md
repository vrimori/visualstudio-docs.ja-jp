---
title: Kubernetes ツールのチュートリアル |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2018
ms.technology: vs-ide-deployment
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- azure
ms.openlocfilehash: b354045ceb464a14ff909a503aa62477c73b983c
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2018
ms.locfileid: "36280878"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Visual Studio の Kubernetes ツールを概要します。

Visual Studio の Kubernetes ツールは、Kubernetes を対象とするコンテナー化されたアプリケーションの開発を合理化に役立ちます。 Visual Studio では、Dockerfile と Helm グラフなど、Kubernetes のデプロイをサポートするために必要なコードとしての構成ファイルを自動的に作成できます。 さらに、Visual Studio から Azure Kubernetes Service (AKS) クラスターに直接発行することができます。

## <a name="prerequisites"></a>前提条件

この新しい機能を活用するには、必要があります。

- 最新のプレビュー [Visual Studio 2017](https://visualstudio.microsoft.com/vs/preview)と Azure 開発ワークロード。

- [For Visual Studio の Kubernetes ツール](https://aka.ms/get-vsk8stools)、個別のダウンロードとして入手できます。

- [Windows の docker](https://store.docker.com/editions/community/docker-ce-desktop-windows)開発用ワークステーションにインストールされている (つまり、実行する Visual Studio)

- Visual Studio から AKS に発行する場合。

    1.  [発行ツール AKS](https://aka.ms/get-vsk8spublish)、個別のダウンロードとして入手できます。

    1.  Azure Kubernetes サービス クラスターの場合。 詳細については、次を参照してください。 [AKS クラスターを作成する](/azure/aks/kubernetes-walkthrough-portal#create-aks-cluster)します。 必ず[クラスターに接続する](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster)開発ワークステーションから。

    1.  Helm CLI の開発ワークステーションにインストールします。 詳細については、次を参照してください。 [Helm のインストール](https://github.com/kubernetes/helm/blob/master/docs/install.md)します。

    1.  Helm は AKS クラスターを構成します。 これを行う方法の詳細については、次を参照してください。 [Helm を構成する方法](/azure/aks/kubernetes-helm#configure-helm)します。

## <a name="create-a-new-kubernetes-project"></a>新しい Kubernetes プロジェクトを作成します。

適切なツールをインストールした後は、Visual Studio を起動し、新しいプロジェクトを作成します。 **クラウド**、選択、 **Kubernetes のコンテナー アプリケーションを**プロジェクトの種類。 このプロジェクトの種類を選択して、 **OK**します。

![新しい Kubernetes アプリ プロジェクトの作成のスクリーン ショット](media/k8s-tools-new-k8s-app.png)

ASP.NET Core の種類は、web アプリケーションを作成し、選択できます。 選択**Web アプリケーション**選択**OK**します。 通常、 **Docker サポートを有効にする**オプションは、このダイアログ ボックスでは表示されません。  Docker のサポートは、Kubernetes のコンテナー アプリケーションに対して既定で有効です。

![Web アプリの選択のスクリーン ショット](media/k8s-tools-web-app-selection-screen.png)

## <a name="add-kubernetes-support-to-an-existing-project"></a>Kubernetes のサポートを既存のプロジェクトに追加します。

または、既存の ASP.NET Core web アプリケーション プロジェクトに、Kubernetes のサポートを追加できます。 これを行う、プロジェクトを右クリックし、選択**追加** > **コンテナー オーケストレーター サポート**します。

![メニュー項目を追加するコンテナー オーケストレーターのスクリーン ショット](media/k8s-tools-add-container-orchestrator.png)

ダイアログ ボックスで、"Kubernetes Helm"を選択し、選択**OK**します。

![ダイアログ ボックスを追加するコンテナー オーケストレーターのスクリーン ショット](media/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Visual Studio を作成します。

新たに作成した後は**Kubernetes のコンテナー アプリケーションを**Kubernetes へのデプロイを容易に、プロジェクトでいくつか追加ファイルを表示するプロジェクトまたは既存のプロジェクトへの Kubernetes コンテナー オーケストレーター サポートの追加。

![コンテナー オーケストレーター サポートを追加した後ソリューション Explorer のスクリーン ショット](media/k8s-tools-solution-explorer.png)

追加されたファイルは次のとおりです。

- この web アプリケーションをホストしているコンテナー イメージを使用すると、Docker を生成する Dockerfile。 後ほど説明するよう Visual Studio ツールはデバッグと Kubernetes に展開するときにこの Dockerfile を活用します。 Docker イメージを直接操作したい場合は、Dockerfile を右クリックし、選択**Docker イメージのビルド**します。

   ![スクリーン ショットの Docker イメージのビルド オプション](media/k8s-tools-build-docker-image.png)

- Helm チャート、および*グラフ*フォルダー。 これらの yaml ファイルは、アプリケーションでは、Kubernetes にデプロイする際の Helm チャートを構成します。 Helm の詳細については、次を参照してください。 [ https://www.helm.sh](https://www.helm.sh)します。

- *azds.yaml*します。 これには、Azure 開発用のスペース、Azure Kubernetes サービスで迅速で反復的なデバッグ エクスペリエンスを提供する新しいサービスの設定が含まれています。 このファイルは、現在使用されていないが、Azure 開発用のスペースで将来使用するために予約されています。

## <a name="publish-to-azure-kubernetes-service-aks"></a>Azure Kubernetes Service (AKS) への公開します。

これらすべてのファイルの場所で使用するがいつもと同じようを作成して、アプリケーション コードをデバッグ、Visual Studio IDE を使用できます。

作成したら、希望どおりに実行されているコードを AKS クラスターに Visual Studio から直接発行することができます。

これを行うには、まず、コンテナー イメージを Azure Container Registry (ACR) を発行する発行プロファイルを設定する必要があります。 AKS は ACR からコンテナー イメージをプルし、クラスターに配置できます。

1. **ソリューション エクスプ ローラー**を右クリックし、*プロジェクト*選択**発行**します。

   ![メニュー項目の発行のスクリーン ショット](media/k8s-tools-publish-project.png)

1. **発行**画面で、選択**Container Registry**発行を対象とし、指示に従って、コンテナー レジストリを選択します。 コンテナー レジストリがまだしていない場合は、選択**新しい Azure コンテナー レジストリの作成**Visual Studio から作成します。 詳細については、次を参照してください。 [Azure Container Registry にコンテナーを発行](#publish-your-container-to-azure-container-registry)します。

   ![Pick 発行ターゲットの画面のスクリーン ショット](media/k8s-tools-publish-to-acr.png)

1. ソリューション エクスプ ローラーでバックアップを右クリックして、*ソリューション* をクリック**Publish to Azure AKS**します。

   ![Azure AKS のメニュー項目のスクリーン ショットの発行](media/k8s-tools-publish-solution.png)

1. 自分のサブスクリプションと、AKS クラスターを選択して、ACR と共に作成したプロファイルを発行します。 次に、 **[OK]** をクリックします。

   ![AKS の画面をスクリーン ショットの発行](media/k8s-tools-publish-to-aks.png)

   これにより、 **Publish to Azure AKS**画面。

1.  選択、**構成 Helm**サーバー上の Helm チャートをインストールするために使用するコマンド行の更新へのリンク。

   ![Helm の構成のスクリーン ショットのリンク](media/k8s-tools-configure-helm.png)

   コマンド行を更新することなど別の Kubernetes コンテキストまたはグラフの名前を指定するカスタムのコマンドライン引数がある場合に便利です。

   ![スクリーン ショットの Helm の構成画面](media/k8s-tools-helm-configure-screen.png)

1. 展開する準備ができたら、クリックして、**発行**AKS にアプリケーションを発行するボタンをクリックします。

   ![Azure AKS 画面のスクリーン ショットに発行します。](media/k8s-tools-publish-screen.png)

おめでとうございます! すべての Kubernetes アプリ開発用 Visual Studio の全機能を使えるようになりました。

## <a name="next-steps"></a>次の手順

読み取ることによって Azure で Kubernetes 開発に関する詳細、 [AKS のドキュメント](/azure/aks)します。