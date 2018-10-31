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
ms.openlocfilehash: 0740abb865856470b80d0706794f8e49423e72b2
ms.sourcegitcommit: 6672a1e9d135d7e5cca3cceea07c6fe5a0871475
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/28/2018
ms.locfileid: "47443520"
---
# <a name="onboard-to-the-visual-studio-subscriptions-administration-portal-after-your-organization-was-migrated"></a>組織を移行した後の Visual Studio サブスクリプション管理ポータルへのオンボード 

以前に Microsoft ボリューム ライセンス サービス センター (VLSC) で Visual Studio サブスクリプションを管理していて、最近サイトにアクセスしてサブスクリプションを管理した場合は、VLSC でサブスクリプションを管理できなくなったことがわかります。 サブスクリプションを管理するプロセスは次のようなものでした。
> [!div class="mx-imgBorder"]
> ![[サブスクリプション] タブが強調表示された Microsoft VLSC のスクリーンショット](_img/post-migration-onboarding/vlsc-subscriptions.png)

しかし、現在は、Visual Studio サブスクリプション管理ポータルと呼ばれる新しいポータルを使ってサブスクリプションを管理します。 通常、組織のボリューム ライセンス契約の主要連絡先または通知連絡先がこの手順を完了します。 それ以外の場合は、次の情報がサブスクリプションの管理にアクセスするのに役立ちます。 

次のいずれかのシナリオが発生する可能性があります。
1.  [主要連絡先がオンボード プロセスを完了しなかった。](#Onboarding-not-completed-by-Primary-Contact)<sup>1</sup> 
2.  [主要連絡先はオンボードを完了しましたが、管理を行うユーザーを管理者として追加しませんでした。そのユーザーの資格情報は VLSC の一覧に含まれていました。](#Primary-Contact-did-not-provide-you-administrator-access) 
3.  [主要連絡先はオンボードを完了しましたが、管理を行うユーザーを管理者として追加しませんでした。そのユーザーの資格情報は VLSC の一覧に含まれていませんでした。](#Your-credentials-were-not-listed-in-VLSC-prior-to-migration)  

<sup>1</sup> 管理を行うユーザーが主要連絡先または通知連絡先で、オンボード プロセスを完了しなかった場合、そのユーザーはシナリオ 1 の手順に従って、組織を設定する必要があります。 

次のセクションでは、これらの各シナリオについて詳しく説明します。 

## <a name="onboarding-not-completed-by-primary-contact"></a>主要連絡先がオンボードを完了しなかった

主要連絡先がオンボード エクスペリエンスを完了しなかった場合は、次の画面が表示されます。 [ボリューム ライセンス サービス センター (VLSC)](https://www.microsoft.com/Licensing/servicecenter/default.aspx) にアクセスできる場合は、このプロセスを完了して、サブスクリプションの管理にアクセスできるようになります。 VLSC で見つかる組織の[パブリック カスタマー番号 (PCN)](find-pcn.md) が必要です。 

PCN フィールドに [PCN](find-pcn.md) を入力して、**[招待メールを送信する]** を選択します。 
> [!div class="mx-imgBorder"]
> ![Visual Studio サブスクリプション管理ポータルのスクリーンショット](_img/post-migration-onboarding/send-invitation.png)

オンボード プロセスを完了するための一意のリンクが記載された電子メールが届きます。 電子メールのリンクをクリックし、自分の電子メール アドレスでサインインして、再度 PCN を入力します。 メールの専用リンクを使うと、Visual Studio サブスクリプション管理ポータルにアクセスできるようになります。 これで、サブスクリプションにアクセスして管理できるようになりました。 
> [!div class="mx-imgBorder"]
> ![成功の通知のスクリーンショット](_img/post-migration-onboarding/email-success.png)


## <a name="primary-contact-did-not-provide-you-administrator-access"></a>主要連絡先がユーザーに管理者アクセスを提供しなかった

主要連絡先がオンボード プロセスを完了し、管理を行うユーザーの資格情報が以前に VLSC に含まれていたが、主要連絡先がユーザーにアクセス許可を付与しなかった場合は、次の通知が表示されます。 管理者になるには、通知の一覧に表示されている組織のスーパー管理者のいずれかに問い合わせます。
> [!div class="mx-imgBorder"]
> ![スーパー管理者の一覧を含む、Visual Studio サブスクリプション管理ポータルのスクリーンショット](_img/post-migration-onboarding/admin-list.png)

## <a name="your-credentials-were-not-listed-in-vlsc-prior-to-migration"></a>管理を行うユーザーの資格情報が移行前に VLSC に一覧に含まれなかった

主要連絡先はオンボードを完了したが、管理を行うユーザーをユーザーとして追加せず、そのユーザーの資格情報がそれまで VLSC の一覧に含まれていなかった場合は、次の通知が表示されます。 [主要連絡先](find-primary-contact.md)に連絡して、ポータルへのアクセスを取得します。 
> [!div class="mx-imgBorder"]
> !["ユーザーが見つからない" 通知を含む、Visual Studio サブスクリプション管理ポータルのスクリーンショット](_img/post-migration-onboarding/cant-find-you.png)