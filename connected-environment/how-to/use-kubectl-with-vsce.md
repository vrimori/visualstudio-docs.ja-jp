---
title: Connected Environment で kubectl を使用する方法 | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 03/12/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Azure でのコンテナーおよびマイクロサービスを使用する迅速な Kubernetes 開発
keywords: Docker、Kubernetes、Azure、AKS、Azure Container Service、コンテナー
manager: douge
ms.openlocfilehash: 138dce09e0d53dc47703b9c6f56a7efda4adc255
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31883528"
---
# <a name="use-kubectl-with-a-connected-environment"></a>Connected Environment で `kubectl` を使用する

Connected Environment 内で Kubernetes にアクセスし、`kubectl` など、既存の Kubernetes ツールを使用できます。

`vsce env create` または `vsce env select` を実行すると、`kubectl` 構成コンテキストが自動的に追加されます。kubectl も VSCE Kubernetes クラスターに接続されるはずです。 次に例を示します。
- 現在のコンテキストを確定する: `kubectl config current-context`
- 使用可能なすべてのコンテキストを一覧表示する: `kubectl config get-contexts`。 VSCE で作成されたクラスターには "vsce-<guid>" のような名前が付けられます。
- コンテキストを変更する: `kubectl config use-context <context-name>`
- Kubernetes ダッシュボードを表示する: `kubectl proxy` を実行し、ブラウザーを起動してこのコマンドが出力するアドレスに移動します (URL に `/ui` を付けると、Kubernetes ダッシュボードに移動します)。
- *mainline* という名前の既定の VSCE スペースで実行されているサービスを一覧表示する: `kubectl get services --namespace=mainline`

