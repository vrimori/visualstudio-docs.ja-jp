---
title: "Visual Studio での Python の使用、手順 6、Git との連携 | Microsoft Docs"
description: "Visual Studio で Python を使用するための基礎となるチュートリアルの手順 6 では、Visual Studio の Git 関連の機能について説明します。"
ms.custom: 
ms.date: 01/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 6ce191ce01a89b7fc743562eaf430656f6952271
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="step-6-working-with-git"></a>手順 6: Git の使用

**前の手順: [パッケージのインストールと Python 環境の管理](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

Visual Studio には、ローカルの Git リポジトリおよび、GitHub や Visual Studio Team Services などのサービス上に存在するものを直接統合できます。 この統合には、リポジトリの複製、変更のコミット、分岐の管理が含まれます。

このトピックでは、既存のプロジェクト用にローカル Git リポジトリを作成する方法について説明します。 リモート Git リポジトリからプロジェクトを作成する方法のチュートリアルについては、「[クイック スタート: Visual Studio で Python コードのリポジトリを複製する](quickstart-03-python-in-visual-studio-project-from-repository.md)」を参照してください。

1. [前の手順](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)のプロジェクトなどを Visual Studio で開き、ソリューションを右クリックして、**[Add Solution to Source Control]\(ソリューションをソース管理に追加\)** を選択します。 Visual Studio によってプロジェクト コードを含むローカル Git リポジトリが作成され、Git に関連するコントロールが Visual Studio のウィンドウの下部にも表示されるようになります。 コントロールには、保留中のコミット、変更、リポジトリの名前と分岐が表示されます。 コントロール上にカーソルを置き、追加情報を表します。

  ![Visual Studio ウィンドウの Git コントロールの上にカーソルを置くと表示される追加情報](media/working-with-git-01.png)

1. **[チーム エクスプローラー]** ウィンドウも表示され、リポジトリ ヘッダーを選択すると、さまざまな Git オプションが表示されます。 次の **[同期]** ウィンドウには、リモート リポジトリに公開するためのオプションが表示されています。

  ![ローカル リポジトリの作成後の Visual Studio のチーム エクスプローラー](media/working-with-git-02.png)

1. **[変更]** を選択し、コミットされていない変更を確認し、必要に応じてそれらをコミットします。

  ![コミットされていない変更を示す Visual Studio のチーム エクスプローラー](media/working-with-git-03.png)

1. **[分岐]** を選択し、分岐を調査して、マージとリベース操作を実行します。

  ![分岐を示す Visual Studio のチーム エクスプローラー](media/working-with-git-04.png)

1. ローカル リポジトリを使用する場合、変更をコミットすると、リポジトリでも直接変更されます。 リモート リポジトリに接続している場合、**[同期]** を選択し、ローカル コミットをプッシュします。

## <a name="going-deeper"></a>詳しい説明

Git の操作の詳細なチュートリアルについては、「[Share your code with Visual Studio 2017 and VSTS Git](/vsts/git/share-your-code-in-git-vs-2017)」 (コードを Visual Studio 2017 および VSTS Git で共有する) を参照してください。

## <a name="tutorial-review"></a>チュートリアルのレビュー

これで、Visual Studio での Python のチュートリアルは完了です。 このチュートリアルでは、次を学習しました。

- プロジェクトの作成と、プロジェクトのコンテンツの参照。
- コード エディターの使用と、プロジェクトの実行。
- 対話型のウィンドウを使用した新しいコードの開発と、そのコードのエディターへの簡単なコピー。
- 完成したプログラムの Visual Studio デバッガーでの実行。
- パッケージのインストールと、Python 環境の管理。
- Git リポジトリでのコードの操作。

以下では、概念および使い方ガイドをご確認ください。

- [Python 向け C++ 拡張機能の作成](working-with-c-cpp-python-in-visual-studio.md)
- [Azure App Service への発行](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [プロファイル](profiling-python-code-in-visual-studio.md)
- [単体テスト](unit-testing-python-in-visual-studio.md)
