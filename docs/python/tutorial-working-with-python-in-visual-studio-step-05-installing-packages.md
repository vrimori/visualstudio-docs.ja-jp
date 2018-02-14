---
title: "Visual Studio での Python の使用、手順 5、パッケージのインストール | Microsoft Docs"
description: "Visual Studio で Python を使用する際の主なチュートリアルの 5 番目の手順です。Python 環境でパッケージを管理する、Visual Studio の機能についてご説明します。"
ms.custom: 
ms.date: 01/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: bb0890d5f9433e1f73039e4036b884d7bfcb7933
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="step-5-installing-packages-in-your-python-environment"></a>手順 5: Python 環境へのパッケージのインストール

**前の手順: [デバッガーでコードを実行する](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

Python 開発者コミュニティは、ユーザーが独自のプロジェクトに組み込むことのできる便利なパッケージを何千も作成してきました。 Visual Studio には、Python 環境内のパッケージを管理するための UI が用意されています。

1. **[表示] > [その他のウィンドウ] > [Python Environments (Python 環境)]** メニュー コマンドを選びます。 ソリューション エクスプローラーへのピアとして **[Python 環境]** ウィンドウが開き、利用可能なさまざまな環境が示されます。 リストには、Visual Studio インストーラーを使用してインストールしたものと、個別にインストールした両方の環境が含まれています。 太字で示されている環境は、新しいプロジェクトに使用される既定の環境です。

  ![[Python Environments (Python 環境)] ウィンドウ](media/environments-default-view-blue.png)

1. 環境の **[概要]** タブからは、環境の対話形式のウィンドウと、環境のインストール フォルダーおよびインタープリターにすばやくアクセスできます。 たとえば、**[対話型ウィンドウを開く]** を選択すると、その特定の環境のインタラクティブ ウィンドウが Visual Studio で表示されます。

1. **[パッケージ]** タブを選択すると、環境に現在インストールされているパッケージのリストが表示されます。

  ![環境にインストールされているパッケージ](media/environments-installed-packages-blue.png)

1. 検索フィールドに `matplotlib` の名前を入力してインストールし、`pip install` を選択します。

  ![環境に matplotlib をインストールする](media/environments-add-matplotlib1.png)

1. 昇格に同意するように求められた場合は、同意します。
 
1. パッケージがインストールされると、[Python 環境] ウィンドウにそのパッケージが表示されます。 アンインストールするには、パッケージの右にある **[X]** 選択します。 

  ![環境での matplotlib のインストール完了](media/environments-add-matplotlib2.png)

  環境の下の小さい進行状況バーは、Visual Studio が新しくインストールしたパッケージに対して、IntelliSense データベースを構築していることを示します。 **[IntelliSense]** タブにはより詳細な情報も表示されます。 データベースが完了するまで、そのパッケージのエディターでオートコンプリートや構文チェックなどの IntelliSense 機能はアクティブになりません。

1. **[ファイル] > [新規] > [プロジェクト]** で、"Python アプリケーション" テンプレートを選択して新しいプロジェクトを作成します。 表示されるコード ファイルに、次のコードを貼り付けて余弦波を作成します。これは前のチュートリアルの手順と似ていますが、今回はグラフィカルにプロットするだけです。

    ```python
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt
    from math import radians

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

1. プログラムをデバッガーを使用して実行 (F5) するか、デバッガーなしで実行 (Ctrl + F5) して、出力を確認します。

  ![matplotlib の出力例](media/environments-add-matplotlib3.png)

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [Git の使用](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

### <a name="going-deeper"></a>詳しい説明

- [Python 環境](managing-python-environments-in-visual-studio.md)
