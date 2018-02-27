---
title: "Visual Studio での Python の使用、手順 0、インストール | Microsoft Docs"
description: "Visual Studio で Python を使用するための基礎となるチュートリアルの手順 0 (前提条件) では、Visual Studio に Python のサポートをインストールする方法について説明します。"
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
ms.openlocfilehash: ca3dccf8a30bb4e1132c0bbc7ea8d8e660ae0f8e
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2018
---
# <a name="install-python-support-in-visual-studio"></a>Visual Studio での Python サポートのインストール

> [!Note]
> 現在、Python のサポートは Visual Studio for Windows でのみ使用できます。Mac と Linux では、Visual Studio Code により、Python のサポートを使うことができます。 「[questions and answers (質問と回答)](overview-of-python-tools-for-visual-studio.md#questions-and-answers)」をご覧ください。

1. Windows 用の最新の Visual Studio 2017 インストーラーをダウンロードして実行します (Python のサポートがあるのは、リリース 15.2 以降です)。 Visual Studio が既にインストールされている場合は、Visual Studio インストーラーを実行し、手順 2 へ進みます。

    > [!div class="nextstepaction"]
    > <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted">Visual Studio 2017 のインストールに関するコミュニティ</a>

    >[!Tip]
    > このコミュニティ版は、個人の開発者、クラス学習、学術研究、オープン ソース開発向けです。 その他の用途には、<a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted">Visual Studio 2017 Professional</a> または <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted">Visual Studio 2017 Enterprise</a> を使用してください。

1. インストーラーによって、ワークロード一覧が表示されます。これは、特定の開発分野の関連オプションのグループです。 Python の場合、**[Python 開発]** ワークロードを選択し、**[インストール]** を選択します。

    ![Visual Studio インストーラーの [Python 開発] ワークロード](media/installation-python-workload.png)

1. Python のサポートをすばやくテストするには、Visual Studio を起動し、Alt+I キーを押して Python Interactive ウィンドウを開き、`2+2` を入力します。 `4` という出力が表示されない場合は、手順を再確認してください。

    ![対話型ウィンドウでの Python のテスト](media/installation-interactive-test.png)

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [手順 1: Python プロジェクトの作成](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>関連項目

- [既存の Python インタープリター用の環境の作成](managing-python-environments-in-visual-studio.md#creating-an-environment-for-an-existing-interpreter)
- [Windows に Visual Studio 2015 の Python サポートをインストールする](installing-python-support-in-visual-studio.md)
- [インストールする場所](installing-python-support-in-visual-studio.md#install-locations)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
