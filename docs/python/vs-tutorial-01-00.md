---
title: "Visual Studio での Python の使用、手順 0 -インストール | Microsoft Docs"
ms.custom: 
ms.date: 11/01/2017
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
ms.workload:
- python
- data-science
ms.openlocfilehash: df12e77f6108e15ea99afec7446fa6406cfd1fe3
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2018
---
# <a name="install-python-support-in-visual-studio"></a>Visual Studio での Python サポートのインストール

> [!Note]
> 現在、Python のサポートは Visual Studio for Windows でのみ使用できます。Mac と Linux では、Visual Studio Code により、Python のサポートを使うことができます。 「[質問と回答](python-in-visual-studio.md#questions-and-answers)」を参照してください。

1. Windows 用の最新の Visual Studio 2017 インストーラーをダウンロードして実行します (Python のサポートがあるのは、リリース 15.2 以降です)。

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
> [手順 1: Python プロジェクトの作成](vs-tutorial-01-01.md)

## <a name="see-also"></a>関連項目

- [既存の Python インタープリター用の環境の作成](python-environments.md#creating-an-environment-for-an-existing-interpreter)
- [Windows に Visual Studio 2015 の Python サポートをインストールする](installation.md)
- [インストールする場所](installation.md#install-locations)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
