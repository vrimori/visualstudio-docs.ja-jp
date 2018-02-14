---
title: "TensorFlow モデルをローカルにトレーニングする"
description: "AI Tools for Visual Studio でローカルに TensorFlow モデルを実行します"
keywords: "AI, Visual Studio, TensorFlow, ローカル"
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: quickstart
ms.devlang: python
ms.service: multiple
ms.workload:
- multiple
ms.openlocfilehash: 395340bbaaafb1a990590ab50e3b0257c221e355
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="train-a-tensorflow-model-locally"></a>TensorFlow モデルをローカルにトレーニングする 

このクイック スタートでは、Visual Studio Tools for AI でローカルに [MNIST](http://yann.lecun.com/exdb/mnist/) データセットを使って TensorFlow モデルをトレーニングします。 MNIST データベースには、60,000 例のトレーニング セットと、手書きの数字の 10,000 例のテスト セットが含まれます。 

## <a name="prerequisites"></a>必須コンポーネント

始める前に、次のものがインストールされていることを確認します。

### <a name="google-tensorflow"></a>Google TensorFlow 

端末で次のコマンドを実行します。 
```cmd
C:\>pip.exe install tensorflow
```

### <a name="numpy-and-scipy"></a>NumPy と SciPy 
[NumPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy) と [SciPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy) をインストールします。 

### <a name="download-sample-code"></a>サンプル コードをダウンロードする
TensorFlow、CNTK、Theano などでディープ ラーニングを始めるためのサンプルを含むこの [GitHub リポジトリ](https://github.com/Microsoft/samples-for-ai)をダウンロードします。 

## <a name="open-solution-and-train-model"></a>ソリューションを開いてモデルをトレーニングする

- Visual Studio を起動し、**[ファイル] > [開く] > [プロジェクト/ソリューション]** の順に選びます。

- ダウンロードしたサンプル リポジトリで **Tensorflow Examples** フォルダーを選び、**TensorflowExamples.sln** ファイルを開きます。 

![プロジェクトを開く](media\tensorflow-local\open-project.png)

![ソリューションを開く](media\tensorflow-local\open-solution.png)

- **ソリューション エクスプローラー**で MNIST プロジェクトを探して右クリックし、**[スタートアップ プロジェクトに設定]** を選びます。

- **[開始]** をクリックします。 

- 出力がコンソールに表示されます。

![コンソールからの出力例](media\tensorflow-local\console-output.png)

> [!div class="nextstepaction"]
> [クラウドで TensorFlow モデルをトレーニングする](tensorflow-vm.md)