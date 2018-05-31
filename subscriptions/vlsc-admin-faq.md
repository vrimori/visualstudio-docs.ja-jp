---
title: VLSC 管理の移行に関する FAQ | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/13/2018
ms.topic: Get-Started-Article
description: ボリューム ライセンス サービス センター管理の移行に関する FAQ
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: e4dda4264ae48903e98166346f9e2569ab1e4da0
ms.sourcegitcommit: 37144589d9f850ff81ec7bfb884429989925a43d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
ms.locfileid: "34336127"
---
# <a name="visual-studio-subscriptions-administration-migration"></a>Visual Studio サブスクリプション管理の移行

これから数か月間で、Visual Studio サブスクリプション (旧称 MSDN サブスクリプション) の管理が変更される予定です。 現在、Visual Studio サブスクリプションはボリューム ライセンスを介して購入できます。購入したサブスクリプションは、ボリューム ライセンス サービス センター ポータル (VLSC) で管理されます。 現在、新しい管理ポータルが作成中です。Visual Studio サブスクリプションは今後この新しいポータルで管理される予定です。 新しいポータルでは、VLSC で提供されている既存の操作に加え、制限なしの一括割り当て、サブスクリプションの追跡とフィルター処理、Azure Active Directory (Azure AD) を利用してアクセスを管理する機能を利用できます。 新しい Visual Studio 管理ポータルは [https://manage.visualstudio.com](https://manage.visualstudio.com) に配置されます。 

> [!Note] 
> この移行は MPSA をご利用のお客様には影響しません。 

## <a name="frequently-asked-questions"></a>よく寄せられる質問

### <a name="why-is-it-changing"></a>変更する理由は何ですか?
新しいポータルでは、Visual Studio サブスクリプション管理のエクスペリエンスを最適化し、購入方法に関係なく、Visual Studio サブスクリプションを管理する単一のエクスペリエンスを作成します。 新しいポータルには、Azure AD を利用し、将来に対応できる新しいプラットフォームがあります。 さらに、操作を簡易化し、管理者の効率を向上するようにユーザー インターフェイスが更新されます。

### <a name="who-will-be-impacted"></a>誰が影響を受けますか? 
有効なボリューム ライセンス契約があり、ボリューム ライセンスを介して Visual Studio サブスクリプションを購入したすべてのお客様がこの変更の影響を受けます。 

### <a name="when-is-it-changing"></a>変更される時期はいつですか?
大規模な移行なので、Visual Studio サブスクリプションの有効なボリューム ライセンス契約があるすべてのお客様が新しい管理ポータルに移行されるまで、段階的に移行される予定です。 移行は 2017 年の第 1 四半期に始まりました。 ボリューム ライセンスをご利用のお客様には、移行が行われる予定の週の前にお知らせします。  

### <a name="does-my-organization-need-to-sign-up-for-azure-active-directory-azure-ad"></a>組織が Azure Active Directory (Azure AD) にサインアップする必要はありますか?
お客様の組織が Azure AD にサインアップする必要はありませんが、いつでもサインアップすることができます。 Azure AD にオンボードする場合は、Azure AD の無料レベルを使用して無料で行うことができます。 Azure Active Directory を使用すると、高いセキュリティ、制御、長期的な信頼性で組織を保護できるようになります。 ただし、Azure AD の準備ができていない場合は、現在と同様に Microsoft アカウント (MSA) を引き続き使用することができます。 

### <a name="how-do-i-know-when-my-organization-will-be-migrated"></a>組織の移行時期はどうすればわかりますか?
主要連絡先と通知連絡先には、移行される 1 週間前にオンボード プロセスを完了するように招待する電子メールが送信されます。 また、サブスクリプション マネージャーにも、主要連絡先と通知連絡先に連絡したことと、オンボードを確実に成功させる方法の詳細が記載された電子メールが送信されます。 詳細については、[組織の主要連絡先と通知連絡先の確認方法](#How-do-I-find-out-who-my-Primary-or-Notices-Contact-is?)に関するページを参照してください。 

### <a name="is-onboarding-different-from-migration"></a>オンボードは移行と異なりますか?
はい。  このプロセスには 2 つのフェーズがあります。 管理者が移行の前に組織をセットアップ (つまりオンボード) することで、作業を中断させないことができます。 組織の情報を移行すると、新しいポータルで Visual Studio サブスクリプションを管理できるようになります。 主要連絡先と通知連絡先が移行前にオンボードしない場合、サブスクリプション マネージャーはブロックされ、オンボード プロセスを完了するまでサブスクリプションを管理できなくなります。 

### <a name="what-is-the-onboarding-process"></a>オンボーディング プロセスとは何ですか?
オンボード プロセスを完了するように招待する電子メールが主要連絡先と通知連絡先に送信されます。 プロセスの手順については、以下を参照してください。 
1.  **PCN を検索してサインインする:**

    a.   電子メールでは、主要ご担当者様および連絡先ご担当者様に、専用のリンク、パブリック カスタマー番号 (PCN) の最後の 3 桁が提供されます。* 

    b.   PCN 全体を取得するには、主要連絡先が VLSC にサインインする必要があります (PCN を見つけるための手順が以下に記載されています)。 

    c.  PCN を入手した後に、サインインするよう要求する一意のリンクを選択する必要があります。 組織が Azure AD にない場合は、職場または学校のアカウント (組織が Azure AD である場合) または Microsoft アカウント (MSA) のいずれかを使用してサインインできます。 

    d.  次に、PCN を入力するように求められます。 

2.  **管理者を設定します。**

    PCN を入力すると、スーパー管理者と管理者 (旧称はサブスクリプション管理者) を追加できるページが表示されます。 サブスクリプションの管理が中断しないように、この手順を組織の移行日よりも前に完了しておくことが理想的です。 

3.  **新しいサブスクリプション管理ポータルへのアクセス:** 組織が移行した後に、スーパー管理者と管理者に、新しいポータルにアクセスして、サブスクリプションの管理を開始するように招待する電子メールが送信されます。 

> [!NOTE] 
> 主要ご担当者様および連絡先ご担当者様が、複数の電子メールを受信した場合、複数の PCN があることを意味しています。 各担当者は、それぞれの電子メールに記載されている固有の PCN のリンクを使用してプロセスを完了する必要があります。 

### <a name="what-is-the-difference-between-a-super-admin-and-an-administrator"></a>スーパー管理者と管理者の違いは何ですか?
主要連絡先と通知連絡先が初めてサインインすると、自動的にスーパー管理者として設定されます。スーパー管理者は、他のスーパー管理者または管理者を追加/削除することでサブスクリプションへの管理者のアクセス権を管理できます。また、サブスクリプションを管理することもできます。 スーパー管理者は、自分以外のスーパー管理者を割り当てることができます。

管理者 (旧称はサブスクリプション マネージャー) はサブスクリプションの管理のみを実行できますが、サブスクリプションの管理にアクセスできるユーザーを制御することはできません。 

### <a name="how-will-i-as-an-administrator-onboard-to-the-new-portal"></a>管理者が新しいポータルにオンボードするにはどうすればよいですか?
組織の主要連絡先と通知連絡先には、固有のリンクが電子メールで送信されます。このリンクをクリックすると、Azure Active Directory (Azure AD) または個人の MSA を利用した職場または学校のアカウントでサインインできるページが表示されます。 サインインした後は、組織のパブリック カスタマー番号 (PCN) または承認番号を入力して契約を確認する必要があります。 各担当者はスーパー管理者に設定され、あなたのように Visual Studio サブスクリプションを管理する他の管理者を追加できるようになります。 

### <a name="where-do-i-manage-subscriptions-if-my-organization-has-been-onboarded-but-hasnt-been-migrated"></a>組織がオンボード済みでも移行されていない場合、どこでサブスクリプションを管理できますか? 
お客様の組織が移行され、新しいポータルで管理する準備が完了したという電子メールが Visual Studio サブスクリプションから送信されるまでは、引き続き VLSC を介してサブスクリプションを管理してください。 

### <a name="where-can-i-locate-my-organizations-public-customer-number-pcn-or-authorization-number"></a>組織のパブリック カスタマー番号 (PCN) または承認番号はどこで確認できますか?
[VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx) にサインインし、**[サブスクリプション]** > **[Visual Studio サブスクリプション]** に移動します。 PCN は **[Agreement/Public Customer Number Results]\(契約/パブリック カスタマー番号の結果\)** の下に表示されます。 PCN を確認する手順については、こちらの[ヘルプ記事](/find-pcn/)を参照してください。 

### <a name="how-do-i-find-out-who-my-primary-or-notices-contact-is"></a>主要連絡先または通知連絡先が誰かを確認するにはどうすればよいですか?
[VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx) にサインインし、**[ライセンス] > [関係サマリー]** に移動し、**[ライセンス ID] > [連絡先]** の順に選択します。 主要連絡先または通知連絡先を確認する手順については、こちらの[ヘルプ記事](find-primary-contact.md)を参照してください。 

### <a name="what-if-my-primary-or-notices-contact-is-gone-no-longer-with-the-company-or-not-available-to-complete-onboarding"></a>主要連絡先または通知連絡先が不在である、退職した、またはオンボードを完了できなくなった場合はどうすればよいですか?
[サポートに連絡し](https://www.visualstudio.com/subscriptions/support/#talktous)、VLSC でサブスクリプションの管理に使用していたメール アドレスを伝えていただく必要があります。 確認が完了すると、サポート担当者がオンボード プロセスのお手伝いできるようになります。 

### <a name="what-will-happen-with-renewing-customers"></a>更新の場合はどうなりますか? 
更新プロセスは移行の影響を受けないため、更新のお客様はサブスクリプションの更新を続ける必要があります。 

### <a name="should-my-organization-wait-to-set-up-a-new-agreement-in-the-new-system-rather-than-renew-an-existing-agreement"></a>組織の既存の契約を更新するのではなく、新しいシステムで新しい契約が成立するまで待つ方がよいですか? 
いいえ。  移行は、契約の作成または更新に影響を与えません。 

### <a name="what-if-my-organizations-agreement-is-in-the-grace-period-during-the-transition-will-they-also-be-migrated"></a>組織の契約が移行の猶予期間中の場合はどうなりますか? これらも移行されますか?
はい。契約がまだ有効な場合、組織は移行されます。 

### <a name="what-if-my-organization-has-over-claimed-in-the-current-system-will-we-still-be-migrated-to-the-new-system"></a>現在のシステムで組織が超過申請した場合はどうなりますか? 新しいシステムには移行されますか? 
はい。お客様の組織は新しいシステムに移行されます。 新しいシステムには、超過申請する機能 (超過申請を許可している契約の種類の場合) があります。 

### <a name="what-if-my-organization-has-more-than-one-subscription-assigned-to-a-single-useremail-address"></a>組織が 1 つのユーザー/メール アドレスに複数のサブスクリプションを割り当てている場合はどうなりますか?
お客様の組織は移行されます。  ただし、同じレベルの追加のサブスクリプション (つまり、エンタープライズ、プロフェッショナルなど) をそのユーザー/メール アドレスに割り当てることはできません。 移行時に同じメール アドレスを持つ同じレベルのサブスクリプションは引き続き表示されますが、管理者はメール アドレスが一意になるように変更する必要があります。 新しいポータルでは、同じレベルの複数のサブスクリプションを 1 つのユーザー/メール アドレスに割り当てることはできません。

### <a name="where-can-i-find-the-most-up-to-date-information-about-the-migration"></a>移行に関する最新情報はどこで確認できますか? 
この移行に関する最新情報は、Visual Studio サブスクリプション管理者用の [Web ページ](https://aka.ms/vs-admin)を参照してください。 サポートが必要な場合は、Visual Studio サブスクリプションの[サポート ページ](http://www.visualstudio.com/subscriptions/support/#!collections/962-subscriptions)を確認してください。このページには、セルフヘルプ情報とサポートの問い合わせ先情報が記載されています。 これから数か月間、この移行を簡単に進めることができるように管理者の Web ページと電子メールで更新情報を提供する予定です。 

## <a name="resources-and-support-information"></a>リソースとサポート情報
- [管理者の Web ページ](https://www.visualstudio.com/subscriptions-administration/)

- Visual Studio のサブスクリプションと管理の[サポート](https://www.visualstudio.com/subscriptions/support/) 

- [PCN を確認する方法](find-pcn.md)

- [主要担当者または通知連絡先を確認する方法](find-primary-contact.md) 

- 組織のオンボードと管理者の管理に関する[ビデオ](https://www.youtube.com/watch?v=ZmnywYGSFMg&list=PLReL099Y5nRfDyvvwzNDBaZe7qTxmuM2T&index=1&t=0s) 
