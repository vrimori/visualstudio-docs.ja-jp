---
title: requirements.txt ファイルを使用したパッケージ要件の管理
description: requirements.txt ファイルを使用して、プロジェクトの依存関係を管理できます。 requirements.txt ファイルを含むプロジェクトを受信した場合は、これらの依存関係を 1 つの手順で簡単にインストールできます。
ms.date: 02/20/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 447eda835a9ea3114f06a6f1a854475191934fad
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="managing-required-packages-with-requirementstxt"></a>requirements.txt での必要なパッケージの管理

ビルド システムを使用してプロジェクトを他のユーザーと共有する場合、または [Microsoft Azure でのプロジェクトの公開](python-azure-cloud-service-project-template.md)を予定している場合は、プロジェクトで必要な外部パッケージを指定する必要があります。 推奨されるアプローチとしては、依存パッケージの必要なバージョンをインストールする pip のためのコマンド リストを含む [requirements.txt ファイル](http://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org) を使います。

技術的には、任意のファイル名を使って要件を追跡できますが (パッケージをインストールするときに `-r <full path to file>` を使って)、Visual Studio では `requirements.txt` に固有のサポートが用意されています。

- `requirements.txt` を含むプロジェクトを読み込み、そのファイルにリストされているすべてのパッケージをインストールする場合は、**ソリューション エクスプローラー**で **[Python 環境]** ノードを展開し、環境ノードを右クリックして **[requirements.txt からインストール]** を選択します。

    ![requirements.txt からインストールする](media/environments-requirements-txt-install.png)

- 既に必要なすべてのパッケージを環境にインストールしている場合は、ソリューション エクスプローラーで環境を右クリックし、**[requirements.txt を生成]** を選択することで、必要なファイルを作成できます。 ファイルが既に存在する場合、更新方法の指定を求められます。

    ![requirements.txt の更新オプション](media/environments-requirements-txt-replace.png)

  - **[Replace entire file (ファイル全体を置き換える)]** は、存在するすべてのアイテム、コメント、オプションを削除します。
  - **[既存のエントリを更新]** は、パッケージの要件を検出し、現在インストールされているバージョンと一致するようにバージョン指定子を更新します。
  - **[Update and add entries (エントリを更新および追加する)]** は、検出されたすべての要件を更新し、他のすべてのパッケージをファイルの末尾に追加します。

`requirements.txt` ファイルは環境の要件を固定するためのものなので、インストールされるすべてのパッケージが正確なバージョンと共に記述されています。 正確なバージョンを使うと、別のコンピューターに環境を簡単に再現できます。 バージョンの範囲、別のパッケージの依存関係、または pip 以外のインストーラーでインストールされたパッケージであってもも、含まれています。

pip でインストールできないパッケージが `requirements.txt` ファイルに出現する場合は、インストール全体が失敗します。 その場合は、ファイルを手動で編集してこのパッケージを除外するか、[pip のオプション](http://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format)を使ってパッケージのインストール可能なバージョンを参照するようにします。 たとえば、[`pip wheel`](http://pip.readthedocs.org/en/latest/reference/pip_wheel.html) を使って依存関係をコンパイルし、`--find-links <path>` オプションを `requirements.txt` に追加することができます。

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

## <a name="see-also"></a>関連項目

- [Visual Studio での Python 環境の管理](managing-python-environments-in-visual-studio.md)
- [プロジェクトのインタープリターの選択](selecting-a-python-environment-for-a-project.md)
- [検索パス](search-paths.md)
- [[Python 環境] ウィンドウ リファレンス](python-environments-window-tab-reference.md)