---
title: VLSC に表示される個人メール
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/23/2018
ms.topic: Get-Started-Article
description: 'Visual Studio のサブスクリプション: サブスクライバーに Hotmail や Gmail のアドレスが表示される理由'
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 3ac8a86bae706b4a68b8e3ccde94a9ee84d608a9
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Visual Studio のサブスクリプション: サブスクライバーに Hotmail や Gmail のアドレスが表示される理由 

ボリューム ライセンス サービス センター (VLSC) から Visual Studio の新しい[サブスクリプション管理ポータル](https://manage.visualstudio.com)に移行すると、一部のサブスクライバーのサインイン用のメール アドレスとして、Hotmail、Gmail や Yahoo などのサードパーティのメール アドレスが表示され、管理者が驚くことがあります。  詳細については、[こちらの動画](https://www.youtube.com/watch?v=1op-i1zEMfY&t=0s&list=PLReL099Y5nRfDyvvwzNDBaZe7qTxmuM2T&index=6)を確認してください。

## <a name="cause"></a>原因

このシナリオは、従来の MSDN サブスクライバー エクスペリエンスにサインイン プロセスが関連付けられていることによって発生します。 ユーザーは Volume License Service Center (VLSC) から新しいポータルに、変更なく移行されました。 管理者は、ユーザーが個人アカウントを使用して、サブスクリプションの特典にアクセスしていたことを知らなかった可能性があります。 2016 年で完了した Visual Studio のサブスクライバーの移行以前は、Visual Studio のサブスクリプションを使用には、2 回アクションを実行する必要がありました。
1. 管理者が、個々のサブスクライバーに、職場または学校のメール アドレスを使用してサブスクリプションを “割り当て” ます。
2. そのサブスクリプションをサブスクライバーが “アクティブ化” します。

サブスクライバーのアクティブ化手順で、サインインに Microsoft アカウント (MSA) が求められます。 サブスクライバーが職場または学校のアカウント (例: tasha@contoso.com) を MSA にしない場合、新しい MSA を作成するか、既存のものが利用されます。 これにより、“サインイン電子メール アドレス” が “割り当てられたメール アドレス” と異なってしまいます。

> [!NOTE] 
> [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) の新しいサブスクライバー エクスペリエンスでは、職場/学校と Microsoft アカウント (MAA) の両種類の ID をサポートしています。

最後に、管理者による移行では、新しいサブスクライバーの管理に使用するサブスクライバーの "サインイン電子メール アドレス" が VLSC のデータから取得されるため、最近移行を行った管理者にとっては、ユーザー インターフェイスの変更によって、以前は気付かなかった個人アカウントがより目立つようになります。

## <a name="solution"></a>ソリューション

この問題を解決するには、サブスクライバーの情報を編集して、サインイン用のメール アドレスを更新する必要があります。  編集はサブスクライバーごとに個々に行うことも、一括で行うことも可能です。 詳細については、「[サブスクリプションを編集する](/visualstudio/subscriptions/edit-license)」を参照してください。  

メール アドレスを更新したら、サインイン情報が変更されたことをサブスクライバーに通知することもできます。  更新された情報が含まれる電子メールも送信されます。   