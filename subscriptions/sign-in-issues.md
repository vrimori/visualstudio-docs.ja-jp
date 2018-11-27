---
title: Visual Studio サブスクリプションへのサインインに関する問題 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 11/07/2018
ms.topic: conceptual
description: Visual Studio サブスクリプションにサインインするときに発生する可能性のある問題について説明します
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 0883e5228a44f0df80e9de912029e21545d5ec2a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51811222"
---
# <a name="issues-signing-in-to-visual-studio-subscriptions"></a>Visual Studio サブスクリプションへのサインインに関する問題
Visual Studio サブスクリプションを使用するには、最初にサインインする必要があります。  サブスクリプションによっては、Microsoft アカウント (MSA) または Azure Active Directory (AAD) ID を使用してセットアップされている場合があります。  この記事では、サブスクリプションにサインインするときに発生する可能性がある問題について説明します。  

## <a name="microsoft-accounts-msa-cannot-be-created-using-workschool-email-addresses"></a>職場/学校のメール アドレスを使用して Microsoft アカウント (MSA) を作成することはできない

職場/学校のメール アドレスを使って新しい個人用 Microsoft アカウント (MSA) を作成する機能は、メール ドメインが Azure AD で構成されているときは使用できません。 この項目の意味 Office 365 または Azure AD に依存する他の Microsoft 提供ビジネス サービスが組織で使用されていて、Azure AD テナントにドメイン名を追加してある場合、ユーザーはドメインのメール アドレスを使って新しい個人用 Microsoft アカウントを作成できなくなります。 

### <a name="why-was-this-change-made"></a>この変更が行われた理由

職場のアドレスをユーザー名として使って個人用 Microsoft アカウントを作成することは、エンド ユーザーにとっても IT 部門にとっても問題があることです。 例: 
- ユーザーは、自分の個人用 Microsoft アカウントがビジネスに準拠していて、自分の OneDrive にビジネス ドキュメントを保存してもポリシーを遵守していると考える可能性があります 
- 組織を離れたユーザーは、通常、職場のメール アドレスにアクセスできなくなります。 そうなったとき、自分のパスワードを忘れた場合、自分の個人用 Microsoft アカウントに戻れなくなる場合があります。 逆に、IT 部門はパスワードをリセットして、退職した従業員の個人用アカウントに入ることができます。 
- IT 部門は、アカウントの所有権とセキュリティに関して誤った認識を持っています。 しかし、ユーザーは、職場のメール アドレスにコードを 1 回ラウンドトリップするだけで、後でいつでも自分のアカウント名を変更できます。 

そのような状況は、同じメール アドレスで 2 つのアカウント (Azure AD と Microsoft アカウント) を持っているユーザーの場合、特に混乱を招きます。 

### <a name="what-does-this-experience-look-like"></a>この場合に表示されるエクスペリエンス

職場または学校のメール アドレスで Microsoft のコンシューマー アプリにサインアップしようとすると、次のようなメッセージが表示されます。 

   > [!div class="mx-imgBorder"]
   > ![職場のメールではアカウントを作成できない](_img/sign-in-issues/cannot-use-work-email.png)

一方、個人用アカウントと職場/学校アカウントをサポートする Microsoft アプリにサインアップしようとすると、次のようなメッセージが表示されます。

   > [!div class="mx-imgBorder"]
   > ![職場/学校アカウントがサポートされている](_img/sign-in-issues/existing-account.png)

### <a name="are-existing-accounts-affected"></a>既存のアカウントへの影響
ここで説明したサインアップのブロックでは、新しいアカウントの作成だけが禁止されます。 職場/学校のメール アドレスで既に Microsoft アカウントを持っているユーザーには影響ありません。 既にそのような状況になっている場合、個人用 Microsoft アカウントの名前を簡単に変更できるようになっています。 簡単なステップ バイ ステップ ガイダンスが、こちらの[サポート記事](http://windows.microsoft.com/en-US/Windows/rename-personal-microsoft-account)で提供されています。 個人用 Microsoft アカウントの名前の変更とはユーザー名を変更することを意味し、職場のメールや、Office 365 などのビジネス サービスへのサインイン方法には影響ありません。 また、個人情報にも影響しません。サインイン方法が変わるだけです。 別の (個人用) メール アドレスを使用したり、新しい @outlook.com メール アドレスを Microsoft から取得したり、自分の電話番号を新しいユーザー名として使用したりすることができます。 

> [!NOTE]
> たとえば Premier サポートなどの Microsoft ビジネス サービスにアクセスするために、IT 部門から職場/学校のメール アドレスで個人用 Microsoft アカウントを作成するよう要求された場合は、アカウントの名前を変更する前に管理チームに連絡します。 

## <a name="deleting-a-sign-in-address-may-prevent-access-to-a-subscription"></a>サインイン アドレスを削除するとサブスクリプションにアクセスできなくなる可能性がある

サブスクリプションに関連付けられている ID (MSA または AAD) を削除した場合、ユーザー名とサインイン ID を含むサブスクライバー情報が匿名になり、サブスクリプションにアクセスできなくなる可能性があります。 

サブスクリプションへのアクセスが影響を受けないようにするには、次のいずれかの方法を使用します。  
- 両方の ID 管理システムではなく、どちらか一方 (MSA または AAD) だけを配置します。  
- テナントを介して、AAD と MSA の ID を関連付けます。 


## <a name="next-steps"></a>次の手順
- AAD 内で [MSA アカウントと AAD アカウントをリンクする](/azure/active-directory/b2b/add-users-administrator)方法を学習します。
- [匿名化](anonymization.md)について詳しく学習します。 
