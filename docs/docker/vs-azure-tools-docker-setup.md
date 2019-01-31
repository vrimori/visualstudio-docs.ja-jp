---
title: VirtualBox を使用した Docker ホストの構成 | Microsoft Docs
description: Docker マシンと VirtualBox を使用して既定の Docker インスタンスを構成する詳細な手順
services: azure-container-service
documentationcenter: na
author: mlearned
manager: jillfra
ms.assetid: 0b1335a2-7720-42a8-8260-4e06fc00c9f6
ms.service: multiple
ms.devlang: dotnet
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: multiple
ms.date: 06/08/2016
ms.author: mlearned
ms.openlocfilehash: a3c02d59021f7596c4c754e185782c591b71fd11
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55140723"
---
# <a name="configure-a-docker-host-with-virtualbox"></a>VirtualBox を使用した Docker ホストの構成
## <a name="overview"></a>概要
この記事では、Docker マシンと VirtualBox を使用して既定の Docker インスタンスを構成する方法を説明します。
[Docker for Windows](https://www.docker.com/products/docker-desktop) を使用している場合、この構成は必要ありません。

## <a name="prerequisites"></a>必須コンポーネント
次のツールをインストールする必要があります。

* [Docker Toolbox](https://github.com/docker/toolbox/releases)

## <a name="configuring-the-docker-client-with-windows-powershell"></a>Windows PowerShell を使用した Docker クライアントの構成
Docker クライアントを構成するには、Windows PowerShell を開き、次の手順を実行します。

1. 既定の Docker ホスト インスタンスを作成します。

    ```PowerShell
    docker-machine create --driver virtualbox default
    ```
2. 既定のインスタンスが構成され、実行されていることを確認します。 (通常は、"default" という名前のインスタンスが実行されていることがわかります)。

    ```PowerShell
    docker-machine ls
    ```

    ![docker-machine ls output](media/vs-azure-tools-docker-setup/docker-machine-ls.png)
3. 現在のホストを既定として設定し、シェルを構成します。

    ```PowerShell
    docker-machine env default | Invoke-Expression
    ```
4. アクティブな Docker コンテナーを表示します。 リストは空にする必要があります。

    ```PowerShell
    docker ps
    ```

    ![docker ps output](media/vs-azure-tools-docker-setup/docker-ps.png)

> [!NOTE]
> 開発用コンピューターを再起動するたびに、ローカルの Docker ホストを再起動する必要があります。
> これを行うには、コマンド プロンプトで、次のコマンドを発行します。`docker-machine start default`
