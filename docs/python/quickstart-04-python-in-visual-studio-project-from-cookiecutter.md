---
title: クイック スタート - Cookiecutter を使用して Python プロジェクトを作成する
description: このクイック スタートでは、Cookiecutter テンプレートを使用して Python プロジェクトを作成します。
ms.date: 12/06/2018
ms.prod: visual-studio-dev15
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 9dd949f921c3d504823e9204e0974617c8a2b3e7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953186"
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>クイック スタート: Cookiecutter テンプレートからプロジェクトを作成する

[Visual Studio 2017 に Python のサポートをインストール](installing-python-support-in-visual-studio.md)すると、GitHub に公開している多くのものを含め、Cookiecutter テンプレートから簡単に新しいプロジェクトを作成できます。 [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) は、テンプレートの検出、テンプレート オプションの入力、プロジェクトとファイルの作成を行うためのグラフィカル ユーザー インターフェイスを提供します。 Cookiecutter は Visual Studio 2017 に付属しており、Visual Studio の以前のバージョンにも個別にインストールできます。

1. このクイック スタートでは、ここに示す Cookiecutter テンプレートに必要な Python パッケージを含む Anaconda3 Python ディストリビューションを最初にインストールします。 Visual Studio インストーラーを実行して、**[変更]** を選択し、右側にある **[Python 開発]** のオプションを展開して、**Anaconda3** (32 ビットまたは 64 ビット) を選択します。 インストールは、インターネットの速度によっては時間がかりますが、これが必要なパッケージをインストールする最も簡単な方法です。

1. Visual Studio を起動します。

1. **[ファイル]** > **[新規]** > **[From Cookiecutter...]\(Cookiecutter から...\)** の順に選択します。 このコマンドによって、テンプレートを参照できるウィンドウが Visual Studio で開きます。

    ![Cookiecutter テンプレートを使用した新しいプロジェクト](media/projects-from-cookiecutter1.png)

1. **Microsoft/python-sklearn-classifier-cookiecutter** テンプレートを選択し、**[次へ]** を選択します。 (Cookiecutter を初めて使用する場合、この手順には数分かかる場合があります。)

1. 次の手順では、**[Create To]\(作成先\)** フィールドに新しいプロジェクトの場所を設定し、**[作成]** を選択します。

    ![Cookiecutter 使用の 2 番目の手順、プロジェクト プロパティの設定](media/projects-from-cookiecutter2.png)

1. 手順が完了すると、"**ファイルが正常に作成されました。**" というメッセージが表示されます。 **[ソリューション エクスプローラーで開く]** のコマンドを選択し、プロジェクトを開きます。

1. **Ctrl** + **F5** キーを押すか、**[デバッグ]** > **[デバッグなしで開始]** の順に選択し、プログラムを実行します。

    ![python-sklearn-classifier-cookiecutter テンプレート プロジェクトの出力](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [チュートリアル: Visual Studio での Python の使用](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>関連項目

- [Cookiecutter 拡張機能の使用](using-python-cookiecutter-templates.md)
- [既存の Python インタープリターを手動で識別する](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Visual Studio 2015 以前の Python サポートをインストールする](installing-python-support-in-visual-studio.md)
- [インストールする場所](installing-python-support-in-visual-studio.md#install-locations)
