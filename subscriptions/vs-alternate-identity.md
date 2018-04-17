---
title: Visual Studio サブスクライバー向けの ID
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 3/15/2018
Ms.topic: Get-Started-Article
Description: How to add an alternate identity for your Visual Studio subscription, to use for VSTS and Azure.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 70bfd305ec35b562fb722fb853016c3df4240ff8
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="identities-for-visual-studio-subscribers"></a>Visual Studio サブスクライバー向けの ID

Visual Studio サブスクリプションをアクティブ化すると、アクティベーション中に使用した ID (またはログイン) が Visual Studio サブスクリプションとリンクされます。 これにより、Microsoft は [Visual Studio サブスクライバー ポータル](https://my.visualstudio.com?wt.mc_id=o~msft~docs)、VSTS、および Azure でユーザーを認識することができます。

VSTS では、ユーザーがログインするたびに Visual Studio サブスクリプションの状態を確認し、メンバーである各アカウント内に自動的に機能を付与します。 これらの機能はサブスクライバーの特典として含まれるため、Visual Studio サブスクリプションにリンクされている ID を使用しているときに、任意の VSTS アカウントのメンバーとして無料で追加されます。

Azure では、サブスクライバーの特典である[月単位の Azure クレジット](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/)をアクティブ化すると、Visual Studio サブスクリプションの状態が確認されます。

[Visual Studio サブスクライバー ポータル](https://my.visualstudio.com?wt.mc_id=o~msft~docs)内で、アクティベーション中に使用した ID に加えて、**代替 ID** を追加できる可能性があります。 現在、サブスクリプションをアクティブ化するために Microsoft アカウントを使用した場合、代替 ID を追加することを許可しています。 この方法で、個人用アカウントと職場または学校アカウントの両方を使用して VSTS にアクセスすることを許可し、(Visual Studio、Office 365、または会社または学校のネットワークにログインするときに使用する) 職場または学校アカウントを追加することもできます。

## <a name="how-to-add-an-alternate-identity-to-your-visual-studio-subscription"></a>Visual Studio サブスクリプションに代替 ID を追加する方法

1. [Visual Studio サブスクライバー ポータル](https://my.visualstudio.com?wt.mc_id=o~msft~docs)にサインインします。

  > "個人用アカウント" または "職場または学校アカウント" の選択を求められた場合は、"個人用アカウント" (自分の Microsoft アカウント) を選びます。
  >
  > Microsoft アカウントと職場または学校アカウントは同じメール アドレスを共有するため、アカウントを選択する必要がある場合があります。 両方の ID で同じメール アドレスを使用しますが、異なるプロファイル、セキュリティ設定、およびアクセス許可を持つ個別の ID になります。
  >
  > 2018 年 3 月 30 日以降、Azure Active Directory で管理されるドメインを使用する電子メールを使用して、Microsoft アカウントを作成することはできなくなります。 この電子メールを職場アカウントとして使用し、引き続きサインインすることができます。

2. **[サブスクリプション]** タブに移動します。

  ![サブスクリプションの選択](_img/vs-alternate-identity/choose-subscriptions-my-visual-studio-com-portal.png)

3. **[関連リンク]** の下にある **[代替アカウントを追加する]** にアクセスします。

  ![[関連リンク] の下にある [代替アカウントを追加する] にアクセスする](_img/vs-alternate-identity/add-alternate-account-my-visual-studio-com-portal.png)

4. 職場または学校アカウントを入力して、**[追加]** を選択します。

  ![職場または学校アカウントを入力する](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. 職場または学校アカウントを使用して、VSTS アカウント (```https://{youraccount}.visualstudio.com```) にサインインします。 情報の反映にわずかな遅延が生じる可能性があるため、15 分後にもう一度確認してください。 

## <a name="faq"></a>FAQ

### <a name="q--why-doesnt-vsts-recognize-me-as-a-visual-studio-subscriber"></a>Q: VSTS で Visual Studio サブスクライバーとして認識されないのはなぜですか?
A: プライマリ ID または代替 ID を使用してサインインすると、VSTS で自動的にサブスクリプションが認識されます。 認識されない場合は、次のいくつかのことを試すことができます。

* [特典として VSTS を含む](vs-vsts.md)アクティブな Visual Studio サブスクリプションがあることを確認します。

* Visual Studio サブスクリプション用のプライマリ ID または代替 ID のいずれかであるログインまたは ID を使用していることを確認します。

* VSTS にサインインする前に、少なくとも 1 回は [Visual Studio サブスクライバー ポータル](https://my.visualstudio.com?wt.mc_id=o~msft~docs)にアクセスします。

引き続き VSTS でサブスクリプションが認識されない場合は、[サポートにお問い合わせください](https://www.visualstudio.com/team-services/support/)。

