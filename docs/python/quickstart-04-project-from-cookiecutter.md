---
title: "クイック スタート: Visual Studio の Cookiecutter テンプレートから Python プロジェクトを作成する | Microsoft Docs"
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7bbb71c-fa07-42e8-bef9-0b9cf6dd628a
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: a877ea77a854659372bfc73b9ef85bc8c81d3be4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>クイック スタート: Cookiecutter テンプレートからプロジェクトを作成する

[Visual Studio 2017 に Python のサポートをインストール](installation.md)すると、GitHub に公開している多くのものを含め、Cookiecutter テンプレートから簡単に新しいプロジェクトを作成できます。 [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) は、テンプレートの検出、テンプレート オプションの入力、プロジェクトとファイルの作成を行うためのグラフィカル ユーザー インターフェイスを提供します。 Cookiecutter は Visual Studio 2017 に付属しており、Visual Studio の以前のバージョンにも個別にインストールできます。

1. このクイック スタートでは、ここに示す Cookiecutter テンプレートに必要な Python パッケージを含む Anaconda3 Python ディストリビューションを最初にインストールします。 Visual Studio インストーラーを実行して、**[変更]** を選択し、右側にある **[Python 開発]** のオプションを展開して、"Anaconda3" (32 ビットまたは 64 ビット) を選択します。 インストールは、インターネットの速度によっては時間がかりますが、これが必要なパッケージをインストールする最も簡単な方法です。

1. Visual Studio を起動します。

1. **[ファイル]、[新規]、[From Cookiecutter...]\(Cookiecutter から...\)** を選択します。このコマンドによって、テンプレートを参照できるウィンドウが Visual Studio で開きます。 

    ![Cookiecutter テンプレートを使用した新しいプロジェクト](media/projects-from-cookiecutter1.png)

1. "Microsoft/python-sklearn-classifier-cookiecutter" テンプレートを選択し、**[次へ]** を選択します。 (Cookiecutter を初めて使用する場合、この手順には数分かかる場合があります。)

1. 次の手順では、**[Create To]\(作成先\)** フィールドに新しいプロジェクトの場所を設定し、**[作成]** を選択します。

    ![Cookiecutter 使用の 2 番目の手順、プロジェクト プロパティの設定](media/projects-from-cookiecutter2.png)

1. 手順が完了すると、"Files created successfully."\(ファイルが正常に作成されました。\) というメッセージが表示されます。 **[ソリューション エクスプローラーで開く]** のコマンドを選択し、プロジェクトを開きます。

1. Ctrl + F5 キーを押すか、**[デバッグ]、[デバッグなしで開始]** を選択し、プログラムを実行します。 

    ![python-sklearn-classifier-cookiecutter テンプレート プロジェクトの出力](media/projects-from-cookiecutter4.png)


## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [チュートリアル: Visual Studio での Python の使用](vs-tutorial-01-01.md)

## <a name="see-also"></a>関連項目

- [Cookiecutter 拡張機能の使用](cookiecutter.md)
- [既存の Python インタープリター用の環境の作成](python-environments.md#creating-an-environment-for-an-existing-interpreter)
- [Windows に Visual Studio 2015 の Python サポートをインストールする](installation.md)
- [インストールする場所](installation.md#install-locations)
