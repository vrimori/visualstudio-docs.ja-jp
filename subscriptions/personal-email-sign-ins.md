---
title: "VLSC に表示される個人メール"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/23/2018
Ms.topic: Get-Started-Article
Description: "Visual Studio Subscriptions – Why Am I Seeing Hotmail or Gmail Addresses for My Subscribers?"
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 2bfe2f39d432be5fc6ff7b24be2a218d02fce961
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2018
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Visual Studio のサブスクリプション: サブスクライバーに Hotmail や Gmail のアドレスが表示される理由 

ボリューム ライセンス サービス センター (VLSC) から Visual Studio の新しい[サブスクリプション管理ポータル](https://manage.visualstudio.com)に移行すると、一部のサブスクライバーのサインイン用のメール アドレスとして、Hotmail、Gmail や Yahoo などのサードパーティのメール アドレスが表示され、管理者が驚くことがあります。

## <a name="cause"></a>原因

このシナリオは、従来の MSDN サブスクライバー エクスペリエンスにサインイン プロセスが関連付けられていることによって発生します。 変更なくユーザーは VLSC から新しいポータルに移行されています。 一部の管理者は、ユーザーが個人アカウントを使用して、サブスクリプションの特典にアクセスしていたことを知りません。 2016 年で完了した Visual Studio のサブスクライバーの移行以前は、Visual Studio のサブスクリプションを使用には、2 回アクションを実行する必要がありました。
1. 管理者が、個々のサブスクライバーに、職場または学校のメール アドレスを使用してサブスクリプションを “割り当て” ます。
2. そのサブスクリプションをサブスクライバーが “アクティブ化” します。

サブスクライバーのアクティブ化処理中には、次が発生します。
1. サインインに Microsoft アカウント (MSA) が求められます。
2. サブスクライバーが職場または学校のアカウント (例: John@contoso.com) を MSA にしない場合、新しい MSA を作成するか、既存のものが利用されます。
3. これにより、“サインイン電子メール アドレス” が “割り当てられたメール アドレス” と異なってしまいます。

> [!NOTE] 
> [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) の新しいサブスクライバー エクスペリエンスでは、職場/学校と Microsoft アカウント (MSA) の両種類の ID をサポートしています。

最後に、管理者による移行では、新しいサブスクライバーの管理に使用するサブスクライバーの “サインイン電子メール アドレス” は VLSC のデータから取得されるため、最近移行を行った管理者は、以前は気付かなかった個人アカウントが UI の変更によってより目立つようになります。

## <a name="solution"></a>ソリューション

この問題を解決するには、サブスクライバーの情報を編集して、サインイン用のメール アドレスを更新する必要があります。  編集はサブスクライバーごとに個々に行うことも、一括で行うことも可能です。 詳細については、「[サブスクリプションを編集する](/visualstudio/subscriptions/edit-license)」を参照してください。  

メール アドレスを更新したら、サインイン情報が変更されたことをサブスクライバーに通知することもできます。  