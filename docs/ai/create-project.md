---
title: "AI Tools for Visual Studio でプロジェクトを作成する"
description: "Azure Machine Learning ギャラリーのサンプルを使ってプロジェクトを作成します"
keywords: AI, Visual Studio, Azure Machine Learning
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: how to article
ms.technology: visual studio
ms.devlang: multiple
ms.service: multiple
ms.openlocfilehash: 2d8b5f1d06d31eaba9c75e0f0515b2526fc7efdf
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
## <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Visual Studio で Azure Machine Learning ギャラリーから AI プロジェクトを作成する

Azure Machine Learning は Visual Studio Tools for AI と統合されています。 これを使って、Azure 仮想マシンや Spark クラスターなどのリモート コンピューター ターゲットに Machine Learning ジョブを送信できます。 詳細については、「[Azure Machine Learning 実験サービスの構成](https://docs.microsoft.com/azure/machine-learning/preview/experimentation-service-configuration)」をご覧ください 

[Visual Studio Tools for AI をインストール](installation.md)すれば、Azure Machine Learning サンプル ギャラリーにある事前に定義されたレシピを使用して新しい Python プロジェクトを容易に作成することができます。

> ! Azure Machine Learning ワークベンチをインストールする必要があります。 インストールについては、「[Azure Machine Learning のインストールに関するクイックスタート](https://docs.microsoft.com/azure/machine-learning/preview/quickstart-installation)」をご覧ください 

1. Visual Studio を起動します。 **[AI Tools]\(AI Tools\)** メニューを開き、**[Select Cluster]\(クラスターの選択\)** を選択して、**サーバー エクスプローラー**を開きます  

    ![クラスターの選択](media\create-project\select-cluster.png)

1. サーバー エクスプローラーで **[Azure Machine Learning]** ノードを右クリックし、**[ログイン]** を選択して指示に従い、Azure Machine Learning サブスクリプションにサインインします。

    ![ログイン](media\create-project\azureml-login.png)
 
2. **[AI Tools]\(AI Tools\) > [Azure Machine Learning Sample Gallery]\(Azure Machine Learning サンプル ギャラリー\)** を選びます。 
    
    ![サンプル ギャラリー](media\create-project\gallery.png)

1. このクイック スタートでは "**MNIST using TensorFlow**" サンプルを選び、**[インストール]** をクリックします。 以下の情報を入力します。 
2.
 - **[Resource Group]\(リソース グループ\)**: メタデータを格納する Azure リソース グループ
 - **[Account]\(アカウント\)**: Azure Machine Learning の実験アカウント
 - **[Workspace]\(ワークスペース\)**: Azure Machine Learning のワークスペース
 - **[Project Type]\(プロジェクトの種類\)**: 機械学習のフレームワーク。 この例では、**[TensorFlow]** を選びます
 - **[Add to Solution]\(ソリューションに追加\)**: 現在の Visual Studio ソリューションに追加するか、新しいソリューションを作成して開くかを指定します
 - **[Project Path]\(プロジェクトのパス\)**: コードを保存する場所
 - **[Project Name]\(プロジェクト名\)**: 「**TensorFlowMNIST**」と入力します
   

    ![Python アプリケーション テンプレートを使用した結果のプロジェクト](media\create-project\new-AzureSampleProject.png)

1. Visual Studio によって、プロジェクト ファイル (ディスク上の `.pyproj` ファイル) と、サンプルで定義されている他のファイルが作成されます。 "MNIST" テンプレートでは、プロジェクトに複数のファイルが含まれます。

    ![mnist](media\create-project\azml-mnist.png)

1. Azure Machine Learning にジョブを送信します。 

    ![mnist](media\create-project\submit-azml.png)

1. Docker コンテナーまたはローカル コンピューターで実行します

    ![mnist](media\create-project\azml-local.png)