---
title: "Visual Studio の IPython REPL | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9bd06b0-2021-4e55-b933-8346476224a8
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 9c0c0124ed508eff8621f946a40c0dda520bc05b
ms.lasthandoff: 03/10/2017

---

# <a name="using-python-in-the-interactive-window"></a>対話型ウィンドウでの Python の使用

Visual Studio の IPython モードの対話型ウィンドウは、対話型の並列コンピューティング機能を備えた高度で使いやすい対話形式の開発環境です。 このトピックでは、Visual Studio の対話型ウィンドウで IPython を使用する方法を説明します。 このため、IPython と必要なライブラリが含まれている [Anaconda](https://www.continuum.io) 環境をインストールする必要があります。

> [!Note]
> Interactive オプション フォームで選択できるにもかかわらず、IronPython は IPython をサポートしていません。 [機能に関する要望](https://github.com/Microsoft/PTVS/issues/84)で賛成票を投じるか、実装することができます。

1. Python のインストール ディレクトリに移動し、Pylab モードで IPython を起動して、IPython パッケージが正しくインストールされていることを確認します。

  ```bash
  ipython --pylab
  ```

1. 次のように入力します。

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r')
  ```

1. すべてが正しく構成されている場合は、次のような出力が表示されます。

    ![IPython 構成の出力 ](~/docs/python/media/ipython-repl-01.png)

1. Visual Studio を開き、Python 環境ウィンドウに切り替え (**[表示]、[その他のウィンドウ]、[Python 環境]** の順に選択)、自分の Python 環境を選択します。
1. **[pip]** タブを見て、`IPython` と `matplotlib` が表示されていることを確認します。 表示されていない場合は、それらをここでインストールします。
1. **[概要]** タブを選択し、**[Configure interactive options (対話オプションの構成)]** を選択します。**[対話モード]** を [IPython] に設定し、**[OK]** を選択します。

    ![対話モードを IPython に設定](~/docs/python/media/ipython-repl-02.png)

1. **[対話型ウィンドウを開く]** を選択して、PyLab で対話型ウィンドウを IPython モードで表示します。 対話モードを変更したばかりの場合は、ウィンドウのリセットが必要なことがあります。

    ![Python モードの対話型ウィンドウ](~/docs/python/media/ipython-repl-03.png)

1. 次のコードを入力します。

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
  ```

1. 最後の行を入力した後、インライン グラフが表示されます (必要であれば、右下隅をドラッグしてサイズを変更できます)。

    ![対話型ウィンドウのインライン グラフ](~/docs/python/media/ipython-repl-04.png)

1. REPL で入力する代わりに、エディターでコードを記述し、コードを選択して右クリックし、**[Interactive に送信]** コマンド (Ctrl + E キー、E) を選択できます。 次のコードをエディターに貼り付け、Ctrl + A で選択し、対話型ウィンドウに送信してみてください  (Visual Studio によってコードが対話型ウィンドウに送信されるとき、途中のグラフやグラフの一部が生成されることを避けるため、コードは&1; つの単位として送信されます)。

    ```python
    from mpl_toolkits.mplot3d import Axes3D
    import matplotlib.pyplot as plt
    import numpy as np
    fig = plt.figure()
    ax = fig.add_subplot(111, projection='3d')
    for c, z in zip(['r', 'g', 'b', 'y'], [30, 20, 10, 0]):
        xs = np.arange(20)
        ys = np.random.rand(20)
        # You can provide either a single color or an array. To demonstrate this,
        # the first bar of each set will be colored cyan.
        cs = [c] * len(xs) 
        cs[0] = 'c' 
        ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)

    ax.set_xlabel('X') 
    ax.set_ylabel('Y') 
    ax.set_zlabel('Z') 
    plt.show()
    ```

    ![エディターから対話型ウィンドウへのコードの送信](~/docs/python/media/ipython-repl-05.png)

1. 対話型ウィンドウ以外にグラフを表示するには、**[デバッグ] の [デバッグなしで開始]** コマンドを使用してコードを実行します。
    
1. IPython には、システム シェルのエスケープ、変数の代入、出力のキャプチャなどの便利な機能が多数あります。詳細については、IPython のリファレンス ガイドを参照してください。

    ![システム シェルのエスケープ](~/docs/python/media/ipython-repl-06.png)

1. IPython は "Notebook" モードで使用することもできます。この場合は、任意の OS で任意のブラウザーをキャンバスとして使用できます。 バック エンドの IPython エンジンは、コンピューター上のローカル エンジンでも、リモート エンジンでもかまいません。 Azure では、[Windows または Linux VM での IPython の実行](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-jupyter-notebook)をサポートしています。 さらに、Azure でのサービスとしての無料の Jupyter Notebooks について、「[Azure Notebooks Preview](https://notebooks.azure.com)」を参照してください。

    ![IPython の Notebook モード](~/docs/python/media/ipython-repl-07.png)

