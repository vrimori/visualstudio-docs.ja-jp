---
title: Visual Studio での Python チュートリアル、手順 5、パッケージのインストール
titleSuffix: ''
description: Visual Studio での Python 機能の中核となるチュートリアルの手順 5 では、Python 環境でパッケージを管理するための Visual Studio の機能について説明します。
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 666b780506784d7c252d37bc018817101bcfede8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53964971"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>手順 5: Python 環境へのパッケージのインストール

**前の手順:[デバッガーでコードを実行する](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

Python 開発者コミュニティは、ユーザーが独自のプロジェクトに組み込むことのできる便利なパッケージを何千も作成してきました。 Visual Studio には、Python 環境内のパッケージを管理するための UI が用意されています。

1. **[表示]** > **[その他のウィンドウ]** > **[Python 環境]** メニュー コマンドを選びます。 **ソリューション エクスプローラー**へのピアとして **[Python 環境]** ウィンドウが開き、利用可能なさまざまな環境が示されます。 リストには、Visual Studio インストーラーを使用してインストールしたものと、個別にインストールした両方の環境が含まれています。 太字で示されている環境は、新しいプロジェクトに使用される既定の環境です。

   ![[Python Environments (Python 環境)] ウィンドウ](media/environments-default-view-blue.png)

2. 環境の **[概要]** タブからは、環境の**対話型**ウィンドウと、環境のインストール フォルダーおよびインタープリターにすばやくアクセスできます。 たとえば、**[対話型ウィンドウを開く]** を選択すると、その特定の環境の**対話型**ウィンドウが Visual Studio で表示されます。

3. **[パッケージ]** タブを選択すると、環境に現在インストールされているパッケージのリストが表示されます。

   ![環境にインストールされているパッケージ](media/environments-installed-packages-blue.png)

4. 検索フィールドに `matplotlib` の名前を入力してインストールし、**pip install** を選択します。

   ![環境に matplotlib をインストールする](media/environments-add-matplotlib1.png)

5. 昇格に同意するように求められた場合は、同意します。

6. パッケージがインストールされると、**[Python 環境]** ウィンドウにそのパッケージが表示されます。 アンインストールするには、パッケージの右にある **[X]** 選択します。

   ![環境での matplotlib のインストール完了](media/environments-add-matplotlib2.png)

   環境の下の小さい進行状況バーが表示され、Visual Studio が新しくインストールしたパッケージに対して、IntelliSense データベースを構築していることを示すことがあります。 **[IntelliSense]** タブにはより詳細な情報も表示されます。 データベースが完了するまで、そのパッケージのエディターでオートコンプリートや構文チェックなどの IntelliSense 機能はアクティブになりません。

   **Visual Studio 2017 バージョン 15.6** 以降では、高速で IntelliSense を操作する異なった方法が使用されています。その効果に関するメッセージが **[IntelliSense]** タブに表示されます。

7. **[ファイル]** > **[新規]** > **[プロジェクト]** で、**Python アプリケーション** テンプレートを選択して新しいプロジェクトを作成します。 表示されるコード ファイルに、次のコードを貼り付けて余弦波を作成します。これは前のチュートリアルの手順と似ていますが、今回はグラフィカルにプロットするだけです。

    ```python
    from math import radians
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

8. プログラムをデバッガーを使用して実行 (**F5** キー) するか、デバッガーなしで実行 (**Ctrl** + **F5** キー) して、出力を確認します。

   ![matplotlib の出力例](media/environments-add-matplotlib3.png)

## <a name="next-step"></a>次のステップ

> [!div class="nextstepaction"]
> [Git の操作](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>詳しい説明

- [Python 環境](managing-python-environments-in-visual-studio.md)
