---
title: Azure Batch AI でモデルをトレーニングするためのジョブを送信する
description: モデル クラウドをトレーニングする
keywords: AI, Visual Studio, モデルのトレーニング, クラウド
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.devlang: multiple
ms.service: multiple
ms.technology: vs-ai-tools
ms.workload:
- azure
ms.openlocfilehash: ec0db69bbde1e2abab7022759ed0f7a3d2a88530
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Azure Batch AI での AI モデルのトレーニング

Batch AI は、データ サイエンティストおよび AI 研究者が、Azure 仮想マシン (GPU がサポートされた VM など) のクラスター上で AI やその他の Machine Learning モデルをトレーニングするための管理対象サービスです。 目的のジョブの要件を記述すると (入力を検索し、出力を格納)、Batch AI が残りの部分を処理します。 Azure Batch AI の詳細については、[こちら](https://docs.microsoft.com/azure/batch-ai/overview)を参照してください。

Azure Batch AI は、Visual Studio Tools for AI に統合されているため、Azure にてトレーニング モデルを動的にスケールアウトすることができます。  [Visual Studio Tools for AI をインストール](installation.md)すれば、Azure Machine Learning サンプル ギャラリーにある事前に定義されたレシピを使用して新しい Python プロジェクトを容易に作成することができます。

1. Visual Studio を起動します。 **[AI Tools]\(AI Tools\)** メニューを開き、**[Select Cluster]\(クラスターの選択\)** を選択して、**サーバー エクスプローラー**を開きます

    ![クラスターの選択](media\train-model\select-cluster.png)


2. **[AI Tools]\(AI Tools\)** を選択します。 所有している Batch AI リソースが自動的に検出され、サーバー エクスプローラーに表示されます。

    ![サンプル ギャラリー](media\train-model\batchai.png)

3. **[ビュー]、[チーム エクスプローラー]** の順に選択し、**[チーム エクスプローラー]** ウィンドウを開きます。ここでは、GitHub または Visual Studio Team Services に接続したり、リポジトリを複製したりできます。

    ![Visual Studio Team Services、GitHub、およびリポジトリの複製が表示された [チーム エクスプローラー] ウィンドウ](media\train-model\team-explorer.png)

4. **[Local Git Repositories]\(ローカル Git リポジトリ\)** の下の [URL] フィールドに、`https://github.com/Microsoft/samples-for-ai` と入力し、複製されたファイル用のフォルダーを入力し、**[複製]** を選択します。

    > [!Tip]
    > チーム エクスプローラーで指定したフォルダーは、複製されたファイルを受け取る特定のフォルダーです。 `git clone` コマンドとは異なり、チーム エクスプローラーで複製を作成しても、リポジトリの名前のサブフォルダーは自動作成されません。

5. 複製が完了したら、**[ファイル]、[ソリューションを開く]、[プロジェクト/ソリューション]** の順にクリックします。

    ![サンプル ギャラリー](media\train-model\open-solution.png)

5. リポジトリを複製したディレクトリで、**samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln** を開きます。

    ![サンプル ギャラリー](media\train-model\tensorflowexamples.png)

5. MNIST プロジェクトを [スタートアップ プロジェクト] として設定

    ![サンプル ギャラリー](media\train-model\mnist-startup.png)

1. MNIST プロジェクトを右クリックし、**[ジョブの送信]** をクリックします。

    ![サンプル ギャラリー](media\train-model\submit-job.png)

1. 目的の **Azure Batch AI** クラスターを選択し、**[インポート]** をクリックします。 `AzureBatchAI_TF_MNIST.json` ファイルを選択します。これにより、使用する Docker イメージなど、いくつかの既定値がすぐに入力されます。 **[送信]** をクリックします。

    ![サンプル ギャラリー](media\train-model\submit-batch.png)