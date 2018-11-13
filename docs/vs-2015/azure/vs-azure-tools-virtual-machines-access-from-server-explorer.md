---
title: サーバー エクスプ ローラーから Azure 仮想マシンへのアクセス |Microsoft Docs
description: Get を表示する方法の概要の作成し、Visual Studio でサーバー エクスプ ローラーで、Azure virtual machines (Vm) を管理します。
author: ghogen
manager: douge
assetId: eb3afde6-ba90-4308-9ac1-3cc29da4ede0
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: e1410b3dc60ec9689b6582e794aaf10cd13092aa
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002352"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>サーバー エクスプローラーから Azure Virtual Machines へのアクセス

Azure でホストされている仮想マシンがある場合は、サーバー エクスプ ローラーでアクセスできます。 必要がありますまずサインインする Azure サブスクリプションに、モバイル サービスを表示します。 サインインすると、サーバー エクスプ ローラーで、Azure ノードのショートカット メニューを開き、選択**Microsoft Azure への接続**します。

1. クラウド エクスプ ローラーで仮想マシンを選択してから、F4 キーをプロパティ ウィンドウを表示します。

    次の表は、どのようなプロパティは、使用できるが、すべて読み取り専用です。 変更するには、使用、 [Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040)します。

   | プロパティ | 説明 |
   | --- | --- |
   | DNS 名 |仮想マシンのインターネット アドレスを含む URL。 |
   | 環境 |仮想マシンでは、このプロパティの値は常に値が実稼働します。 |
   | 名前 |仮想マシンの名前。 |
   | サイズ |利用可能なメモリとディスク領域の量を反映する仮想マシンのサイズ。 詳細については、次を参照してください。[仮想マシンのサイズ](https://docs.microsoft.com/azure/cloud-services/cloud-services-sizes-specs)します。 |
   | Status |値には、開始、開始、停止、停止、および状態の取得が含まれます。 状態を取得する場合は、現在の状態が不明です。 このプロパティの値で使用されている値と異なる、 [Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040)します。 |
   | SubscriptionID |Azure アカウントのサブスクリプション ID。 この情報を表示することができます、 [Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040)サブスクリプションのプロパティを表示します。 |
2. エンドポイント ノードを選択し、表示、**プロパティ**ウィンドウ。
3. 次の表は、エンドポイントの使用可能なプロパティが読み取り専用です。 を追加または仮想マシンのエンドポイントを編集するには使用、 [Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040)します。 

   | プロパティ | 説明 |
   | --- | --- |
   | 名前 |エンドポイントの識別子。 |
   | プライベート ポート |ネットワーク アクセスをアプリケーションの内部ポートです。 |
   | プロトコル |プロトコル エンドポイントのトランスポート層で使用される TCP または UDP のいずれか。 |
   | パブリック ポート |アプリケーションへのパブリック アクセスに使用されるポート。 |
