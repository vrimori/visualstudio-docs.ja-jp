---
title: 組織を移行した後の Visual Studio サブスクリプション管理ポータルへのオンボード
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 07/12/2018
Ms.topic: Get-Started-Article
Description: Learn how to successfully onboard your organization for Visual Studio subscriptions after migrating to the administration portal.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 4052d04669327ab0383aba91de05e4d8b95db4c5
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637456"
---
# <a name="onboarding-to-the-visual-studio-subscriptions-administration-portal-after-your-organization-was-migrated"></a>組織を移行した後の Visual Studio サブスクリプション管理ポータルへのオンボード 

以前にボリューム ライセンス サービス センター (VLSC) で Visual Studio サブスクリプションを管理していて、最近サイトにアクセスしてサブスクリプションを管理した場合は、VLSC でサブスクリプションを管理できなくなったことがわかります。 サブスクリプションを管理するプロセスは次のようなものでした。
> [!div class="mx-imgBorder"]
> ![VLSC サブスクリプション](_img/post-migration-onboarding/vlsc-subscriptions.png)

サブスクリプション ページにアクセスして次のリンクをクリックします。 
> [!div class="mx-imgBorder"]
> ![リレーションシップ概要リンク](_img/post-migration-onboarding/relationship-summary-link.png)

これにより、以前はサブスクリプション管理ページに移動しました。   しかし、現在は、Visual Studio サブスクリプション管理ポータルと呼ばれる新しいポータルを使ってサブスクリプションを管理します。  組織のボリューム ライセンス契約の主要連絡先または通知連絡先は、いくつかの手順を実行する必要があります。 主要連絡先または通知連絡先が、このプロセスを完了しなかった場合、またはいなくなった場合は、いくつかのシナリオが発生する可能性があります。 以下では、サブスクリプションの管理にアクセスできるようにするための手順について説明します。 

次のいずれかのシナリオが発生する可能性があります。
1.  [主要連絡先がオンボード プロセスを完了しませんでした](#Onboarding-not-completed-by-Primary-Contact)<sup>1</sup> 
2.  [主要連絡先はオンボードを完了しましたが、管理を行うユーザーを管理者として追加しませんでした。そのユーザーの資格情報は VLSC の一覧に含まれていました。](#Primary-Contact-did-not-provide-you-administrator-access) 
3.  [主要連絡先はオンボードを完了しましたが、管理を行うユーザーを管理者として追加せず、そのユーザーの資格情報は VLSC の一覧に含まれていませんでした。](#Your-credentials-were-not-listed-in-VLSC-prior-to-migration)  

<sup>1</sup> 管理を行うユーザーが主要連絡先または通知連絡先で、オンボード プロセスを完了しなかった場合、そのユーザーはシナリオ 1 の手順に従って、組織を設定する必要があります。 

以下では、シナリオごとに、表示される可能性がある画面と実行できる手順の例を示します。 

## <a name="onboarding-not-completed-by-primary-contact"></a>主要連絡先がオンボードを完了しなかった

主要連絡先がオンボード エクスペリエンスを完了しなかった場合は、次の画面が表示されます。 [ボリューム ライセンス サービス センター (VLSC)](https://www.microsoft.com/Licensing/servicecenter/default.aspx) にアクセスできる場合は、このプロセスを完了して、サブスクリプションの管理にアクセスできるようになります。 VLSC で見つかる組織の[パブリック カスタマー番号 (PCN)](find-pcn.md) が必要です。 

主要連絡先がオンボード プロセスを完了しなかった場合は、[PCN](find-pcn.md) をフィールドに入力して [招待の送信] を選択するだけです。 
> [!div class="mx-imgBorder"]
> ![招待メールを送信する](_img/post-migration-onboarding/send-invitation.png)

ボタンをクリックして招待を送信すると、ユーザーはオンボード プロセス完了専用のリンクを含むメールを受け取ります。 ユーザーは、メールのリンクをクリックし、自分のメール アドレスでサインインして、再度 PCN を入力する必要があります。 メールの専用リンクを使うと、Visual Studio サブスクリプション管理ポータルにアクセスできるようになります。 その後は、サブスクリプションにアクセスして管理できます。 
> [!div class="mx-imgBorder"]
> ![成功メール](_img/post-migration-onboarding/email-success.png)


## <a name="primary-contact-did-not-provide-you-administrator-access"></a>主要連絡先がユーザーに管理者アクセスを提供しなかった

主要連絡先がオンボード プロセスを完了し、管理を行うユーザーの資格情報が以前に VLSC に含まれていたが、主要連絡先がユーザーにアクセス許可を付与しなかった場合は、ユーザーが [Visual Studio サブスクリプション管理ポータル](https://manage.visualstudio.com/)にサインインすると、次の通知が表示されます。  管理者になるには、画面に表示されている組織のスーパー管理者のいずれかに問い合わせる必要があります。
> [!div class="mx-imgBorder"]
> ![管理者の一覧](_img/post-migration-onboarding/admin-list.png)

## <a name="your-credentials-were-not-listed-in-vlsc-prior-to-migration"></a>管理を行うユーザーの資格情報が移行前に VLSC に一覧に含まれなかった

主要連絡先はオンボードを完了したが、管理を行うユーザーをユーザーとして追加せず、そのユーザーの資格情報がそれまで VLSC の一覧に含まれていなかった場合は、[Visual Studio サブスクリプション管理ポータル](https://manage.visualstudio.com/)にアクセスしようとすると、次の通知が表示されます。 ユーザーは[主要連絡先](find-primary-contact.md)に連絡し、ポータルにアクセスできるようにしてもらう必要があります。 
> [!div class="mx-imgBorder"]
> ![ユーザーが見つからない](_img/post-migration-onboarding/cant-find-you.png)