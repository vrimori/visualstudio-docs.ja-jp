---
title: 開発環境を共有する方法 | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 3/12/2018
ms.topic: article
ms.technology: vsce-kubernetes
description: Azure でのコンテナーおよびマイクロサービスを使用する迅速な Kubernetes 開発
keywords: Docker、Kubernetes、Azure、AKS、Azure Container Service、コンテナー
manager: ghogen
ms.openlocfilehash: 9808e1ac3a6d7b3381b807bc0ce209e15f3e97cf
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
---
# <a name="share-a-development-environment"></a>開発環境の共有

Connected Environment を利用すると、自分の開発環境をチームの他の開発者と共有できます。 開発者はそれぞれ、他の開発者の邪魔をすることなく、自分のスペースで作業できます。 また、1 つの環境で共同作業することで、モックを作成したり、依存関係をシミュレーションしたりすることなく、コードをエンドツーエンドでテストできます。 詳細については、「[チーム開発について学習する](../get-started-nodejs-06.md)」ガイドを参照してください。

複数の開発者のために 1 つの環境を構築するには:
1. [Azure で Connected Environment を作成します](../get-started.md)。 選択した Azure サブスクリプションの所有者または共同作業者アクセスが必要です。
1. 各チーム メンバーに[共同作業者アクセスが与えられる](https://docs.microsoft.com/en-us/azure/active-directory/role-based-access-control-configure)ように環境の**リソース グループ**を構成します。 コマンド `vsce env list` を実行すると、環境のリソース グループを確認できます。
1. 環境内で開発するためにその**環境を選択する**ようにチーム メンバーに依頼します。
     * **コマンド ラインまたは VS Code**: アクセスが与えられた既存の Connected Environments を見るには: `vsce env list`。 環境を選択するには: `vsce env select`。
     * **Visual Studio IDE**: Visual Studio でプロジェクトを開き、起動設定ドロップダウンから **[Connected Environment for AKS]** を選択します。 ダイアログが開いたら、既存の開発環境を選択します。

![Visual Studio の起動設定ドロップダウン](../images/LaunchSettings.png)