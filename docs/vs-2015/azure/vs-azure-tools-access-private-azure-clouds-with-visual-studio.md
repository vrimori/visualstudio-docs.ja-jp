---
title: Visual Studio での Azure プライベート クラウドへのアクセス |Microsoft Docs
description: Visual Studio を使用してプライベート クラウドのリソースにアクセスする方法について説明します。
author: ghogen
manager: douge
assetId: 9d733c8d-703b-44e7-a210-bb75874c45c8
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/13/2017
ms.author: ghogen
ms.openlocfilehash: 216b85e0ebf42b79c388ce217d548f2dce3c86b6
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002962"
---
# <a name="accessing-private-azure-clouds-with-visual-studio"></a>Visual Studio での Azure プライベート クラウドへのアクセス

既定では、Visual Studio は、Azure クラウド REST エンドポイントをサポートします。 この記事では、プライベート クラウドの証明書を使用してアクセスし、Visual Studio からプライベート クラウドと対話する方法について説明します。

1. プライベート クラウドの Azure portal で、発行設定ファイルをダウンロードまたは発行設定ファイルを管理者に問い合わせてください。 (ファイルは、拡張機能を持つ`.publishsettings`)。

1. Visual Studio で**サーバー エクスプ ローラー**を右クリックし、 **Azure**ノード**フィルター サブスクリプションの管理および**します。

    ![サブスクリプションのコマンドを管理します。](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790778.png)

1. **Microsoft Azure サブスクリプションの管理**ダイアログ ボックスで、**証明書**タブを選び**インポート**します。

    ![Azure 証明書のインポート](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790779.png)

1. **Microsoft Azure サブスクリプションのインポート**ダイアログ ボックスで、**参照**します。

    ![[参照] ボタン、[Microsoft Azure サブスクリプションのインポート] ダイアログ](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/browse-button.png)

1. **オープン**ダイアログで、発行設定ファイルを保存したディレクトリを見つけますクリックして、ファイルを選択します**オープン**します。

    ![発行設定ファイルを選択します。](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/select-publish-settings-file.png)

1. 返されるとき、 **Microsoft Azure サブスクリプションのインポート**ダイアログ ボックスで、**インポート**します。

    ![発行設定ファイルのインポート](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790780.png)

    証明書は、Visual Studio に、発行設定ファイルからインポートし、プライベート クラウドのリソースと対話できるようになりました。

