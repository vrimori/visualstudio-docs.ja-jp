---
title: Visual Studio のロックを解除する方法 | Microsoft Docs
ms.custom: ''
ms.date: 07/20/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3bbdab7001ba8724c888b9fc20291ef253f73d4c
ms.sourcegitcommit: fb1fede41d8c5e459dd222755b0497b9d361bc51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="how-to-unlock-visual-studio"></a>Visual Studio のロックを解除する方法

Visual Studio は最大で 30 日間無料で評価できます。 IDE にサインインすると、試用期間が 90 日に延長されます。 Visual Studio の使用を続けるには、次のいずれかの方法で IDE のロックを解除します。

- オンライン サブスクリプションを使用する。

- プロダクト キーを入力する。

## <a name="to-unlock-visual-studio-using-an-online-subscription"></a>オンライン サブスクリプションを使用して Visual Studio のロックを解除するには

Microsoft アカウントか、職場または学校のアカウントに関連付けられた MSDN または Visual Studio Team Service サブスクリプションを使用して Visual Studio のロックを解除するには、次の手順を実行します。

1. IDE の右上隅にある [サインイン] ボタンをクリックします (または、[ファイル]、[アカウントの設定] の順に移動して [アカウントの設定] ダイアログを開き、[サインイン] ボタンをクリックします)。

1. Microsoft アカウントか、職場または学校のアカウントの資格情報を入力します。 Visual Studio は、アカウントに関連付けられている Visual Studio サブスクリプションまたは Visual Studio Team Services サブスクリプションを検索します。

> [!IMPORTANT]
> チーム エクスプローラーのツール ウィンドウから Visual Studio Team Services アカウントに接続すると、Visual Studio は関連付けられているオンライン サブスクリプションを自動的に検索します。 Visual Studio Team Services アカウントに接続した場合は、Microsoft アカウントか、職場または学校アカウントの両方を使用してサインインできます。 そのユーザー アカウントのオンライン サブスクリプションが存在する場合は、Visual Studio は自動的に IDE のロックを解除します。

## <a name="to-unlock-visual-studio-with-a-product-key"></a>プロダクト キーを使って Visual Studio のロックを解除するには

1. **[ファイル]**、**[アカウントの設定]** の順に選択して [アカウントの設定] ダイアログを開き、**[プロダクト キーを使用してライセンスを取得します]** リンクをクリックします。

所定の場所にプロダクト キーを入力します。

> [!TIP]
> Visual Studio のプレリリース版には、プロダクト キーはありません。 プレリリース版を使用するには、IDE にサインインする必要があります。

## <a name="address-license-problem-states"></a>ライセンスの問題状態に対応する

### <a name="update-stale-licenses"></a>古いライセンスを更新する

 Visual Studio でライセンスが古くなっていることを示す次のようなメッセージが表示されることがあります: "ライセンスが古くなったため、更新する必要があります。"

 ![Visual Studio の古いライセンスに関するメッセージ](../ide/media/vs2017_stale-license.png)

 このメッセージは、使用しているサブスクリプションはまだ有効だが、サブスクリプションを最新の状態に維持するために Visual Studio が使用するライセンス トークンが更新されなかったため、次のいずれかの理由でライセンス トークンが古くなったことを示します。

- 長期間にわたって Visual Studio を使用しなかったか、インターネット接続がなかった。
- Visual Studio からサインアウトした。

ライセンス トークンの有効期限が切れる前に、はじめに資格情報の再入力を求めるメッセージが Visual Studio により表示されます。

資格情報を再入力しない場合、トークンの有効期限が近づきます。この場合、[アカウントの設定] ダイアログで、トークンの有効期限が完全に切れるまでの日数が通知されます。 トークンの有効期限が切れた後は、このアカウントの資格情報またはライセンスを前述の別の方法で再入力しないと、Visual Studio の使用を続行できなくなります。

> [!Important]
> インターネットへのアクセスが限定的またはアクセスできない環境で長期間にわたって Visual Studio を使用している場合は、Visual Studio の中断を回避するためにプロダクト キーを使用してロックを解除する必要があります。

### <a name="update-expired-licenses"></a>有効期限が切れたライセンスを更新する

 サブスクリプションの有効期限が完全に切れ、Visual Studio へのアクセス権がなくなった場合は、サブスクリプションを更新するか、サブスクリプションのある別のアカウントを追加する必要があります。 使用中のライセンスの詳細については、**[ファイル]**、**[アカウントの設定]** の順に移動し、ダイアログの右側にあるライセンス情報を参照してください。 異なるアカウントに関連付けられている別のサブスクリプションがある場合は、**[アカウントの追加...]** リンクを選択して、ダイアログ ボックスの左側にある **[すべてのアカウント]** 一覧にそのアカウントを追加します。

## <a name="see-also"></a>関連項目

* [Visual Studio へのサインイン](../ide/signing-in-to-visual-studio.md)
