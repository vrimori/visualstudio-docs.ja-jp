---
title: "Visual Studio の IPython REPL | Microsoft Docs"
ms.custom: 
ms.date: 07/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 856e8b3f13c5938dd6bd7ec1465bda9715636875
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="using-ipython-in-the-interactive-window"></a>対話型ウィンドウでの IPython の使用

Visual Studio の IPython モードの対話型ウィンドウは、対話型の並列コンピューティング機能を備えた高度で使いやすい対話形式の開発環境です。 このトピックでは、Visual Studio の対話型ウィンドウで IPython を使用する手順について説明します。IPython でも、通常の[対話型ウィンドウ](interactive-repl.md)機能をすべて使用できます。

このチュートリアルでは、IPython と必要なライブラリが含まれている [Anaconda](https://www.continuum.io) 環境をインストールする必要があります。

> [!Note]
> Interactive オプション フォームで選択できるにもかかわらず、IronPython は IPython をサポートしていません。 詳細については、[機能要求](https://github.com/Microsoft/PTVS/issues/84)のページを参照してください。

1. Visual Studio を開き、Python 環境ウィンドウに切り替え (**[表示]、[その他のウィンドウ]、[Python 環境]** の順に選択)、IPython を開始したときに表示された Python 環境を選択します。

1. **[パッケージ]** (または **[pip]**) タブを見て、`IPython` と `matplotlib` が表示されていることを確認します。 表示されていない場合は、それらをここでインストールします。

1. **[概要]** タブを選択し、**[IPython 対話モードを使用する]** を選択します (Visual Studio 2015 で **[Configure interactive options]\(対話オプションの構成\)** を選択して **[オプション]** ダイアログを開き、**[インタラクティブ モード]** を IPython に設定し、**[OK]** を選択します)。    

1. **[対話型ウィンドウを開く]** を選択して、対話型ウィンドウを IPython モードで表示します。 対話型モードを変更した場合、ウィンドウのリセットが必要な可能性があります。たとえば、>>> プロンプトのみが表示されている場合、Enter キーを押して更新することができます。

    ![Python モードの対話型ウィンドウ](media/ipython-repl-03.png)

1. 次のコードを入力します。

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
  ```

1. 最後の行を入力した後、インライン グラフが表示されます (必要であれば、右下隅をドラッグしてサイズを変更できます)。

    ![対話型ウィンドウのインライン グラフ](media/ipython-repl-04.png)

1. REPL で入力する代わりに、エディターでコードを記述し、コードを選択して右クリックし、**[Interactive に送信]** コマンド (または Ctrl + E キー) を選択できます。 次のコードをエディターの新しいファイルに貼り付け、Ctrl + A で選択し、対話型ウィンドウに送信してみてください (中間のグラフや部分的なグラフが表示されないように、Visual Studio からはコードが 1 つの単位として送信されます)。 また、別の環境で開いた Python オブジェクトを選択していない場合、**[Python 環境]** ウィンドウの既定としてどの環境が選択されている場合でも、Visual Studio では対話型ウィンドウが開きます。

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

    ![エディターから対話型ウィンドウへのコードの送信](media/ipython-repl-05.png)

1. 対話型ウィンドウ以外にグラフを表示するには、**[デバッグ] の [デバッグなしで開始]** コマンドを使用してコードを実行します。
    
IPython には、システム シェルのエスケープ、変数の代入、出力のキャプチャなどの便利な機能が多数あります。詳細については、[IPython のドキュメント](http://ipython.org/documentation.html)を参照してください。

## <a name="related-topics"></a>関連トピック

- Jupyter をインストールせずに簡単に使用するには、無料の [Azure Notebooks ホスト サービス](https://notebooks.azure.com/)を試してください。ノートブックを保存し、他のユーザーと共有することができます。

- また、Jupyter (旧 IPython) は、Azure 上の自分の Windows または Linux 仮想マシンでも実行できます。 詳細については、「[Azure 上で Azure VM を作成し、Jupyter をインストールして、Jupyter Notebook を実行する](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-jupyter-notebook)」を参照してください。
