---
title: Connected Environment で kubectl を使用する方法 | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 03/12/2018
ms.topic: article
ms.technology: vsce-kubernetes
description: Azure でのコンテナーおよびマイクロサービスを使用する迅速な Kubernetes 開発
keywords: Docker、Kubernetes、Azure、AKS、Azure Container Service、コンテナー
manager: ghogen
ms.openlocfilehash: 46c69f80e58a4265aa5e4320e731c3ad241a8116
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
---
# <a name="use-kubectl-with-a-connected-environment"></a>Connected Environment で `kubectl` を使用する

Connected Environment 内で Kubernetes にアクセスし、`kubectl` など、既存の Kubernetes ツールを使用できます。

`vsce env create` または `vsce env select` を実行すると、`kubectl` 構成コンテキストが自動的に追加されます。kubectl も VSCE Kubernetes クラスターに接続されるはずです。 次に例を示します。
- 現在のコンテキストを確定する: `kubectl config current-context`
- 使用可能なすべてのコンテキストを一覧表示する: `kubectl config get-contexts`。 VSCE で作成されたクラスターには "vsce-<guid>" のような名前が付けられます。
- コンテキストを変更する: `kubectl config use-context <context-name>`
- Kubernetes ダッシュボードを表示する: `kubectl proxy` を実行し、ブラウザーを起動してこのコマンドが出力するアドレスに移動します (URL に `/ui` を付けると、Kubernetes ダッシュボードに移動します)。
- *mainline* という名前の既定の VSCE スペースで実行されているサービスを一覧表示する: `kubectl get services --namespace=mainline`

