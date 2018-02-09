---
title: "別名を使用した Visual Studio サブスクリプションへのサインインが失敗する場合がある | Microsoft Docs"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/2/2018
Ms.topic: Get-Started-Article
Description: Sign-in may fail if aliases or friendly names are used.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 8c07bc8d3cf674d86c2152ff80f20e4fac003fc3
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2018
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-with-aliases"></a>別名を使用した Visual Studio サブスクリプションへのサインインが失敗する場合がある

サインインに使用されるアカウントの種類によっては、[https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) にサインインするときに利用可能なサブスクリプションが正しく表示されない場合があります。考えられる原因の 1 つは、サブスクリプションが割り当てられているサインイン ID の代わりに "別名" または "表示名" を使用していることです。 これは "別名定義" と呼ばれます。 

## <a name="what-is-aliasing"></a>別名定義とは

"別名定義" という用語は、Windows (または Active Directory) へのサインインと電子メールへのアクセスに別々の ID を持っているユーザーを指します。

別名定義は、JohnD@contoso.com のように、会社が自社のディレクトリのサインイン用に Microsoft オンライン サービスを持っているが、ユーザーは John.Doe@contoso.com などの別名や表示名を使用して自分の電子メール アカウントにアクセスしている場合に発生する場合があります。ボリューム ライセンス サービス センター (VLSC) を介してサブスクリプションを管理している多くのユーザーにとって、これがサインインが失敗する原因となる場合があります。指定したメール アドレス (John.Doe@contoso.com) が、"職場または学校アカウント" オプションを通じて正常に認証するために必要なディレクトリ アドレス (JohnD@contoso.com) と一致していないからです。

## <a name="as-an-administrator-what-options-do-i-have"></a>管理者として選択できるオプションとは

管理者には、[https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) でユーザーのサインインを確実に成功させるために、次の 2 つのオプションがあります。 
1. 1 番目のオプション (推奨) は、ディレクトリ アカウントをボリューム ライセンス サービス センター (VLSC) で割り当てられたアドレスとして利用することです。 詳細については、この記事の「[サブスクライバーをディレクトリ アカウントに割り当てる](#assigning-subscribers-to-a-directory-account)」セクションを参照してください。
2. 2 番目のオプション (安全性で劣る) は、サブスクライバーに自身の "職場または学校" のメール アドレスを "個人用" アカウント (別名:  Microsoft アカウント (MSA)) に関連付けることを許可することです。 詳細については、この記事の「[職場または学校アカウントを個人用アカウントとして定義する](#defining-a-work-or-school-account-as-a-personal-account )」セクションを参照してください。

> [!NOTE]
> 会社が新しい Visual Studio サブスクリプションの[管理ポータル](https://manage.visualstudio.com)に移行すると、ディレクトリとメール アドレスの両方をサブスクライバーのプロファイルの一部として指定できる、新しい管理エクスペリエンスが利用できるようになります。  移行の詳細については、[こちら](https://support.microsoft.com/help/4013930/visual-studio-subscriptions-administrator-migration-details)をご覧ください。

## <a name="as-a-subscriber-what-options-do-i-have"></a>サブスクライバーとして選択できるオプションとは

サブスクライバーの観点からは、まず、管理者に問い合わせて、会社の ID の構成を理解することが重要です。  必要に応じて、管理者が管理ポータルから、サブスクライバーのアカウント設定を更新する必要がある場合や、サブスクライバーが自分の会社のメール アドレスを使用して Microsoft アカウント (MSA) を作成する必要がある場合があります。  MSA を作成する手順を実行する前に、この実行に関するポリシーまたは問題について管理者と話します。  詳細については、この記事の「[職場または学校アカウントを個人用アカウントとして定義する](#defining-a-work-or-school-account-as-a-personal-account )」セクションを参照してください。  

## <a name="assigning-subscribers-to-a-directory-account"></a>サブスクライバーをディレクトリ アカウントに割り当てる 

いずれのケースでも、ボリューム ライセンス サービス センター (VLSC) 内のサブスクリプション マネージャーは、新しいサブスクライバーのディレクトリ アドレスを使用するか、"既存の" サブスクライバーの電子メール アドレスを更新する必要があります。  ディレクトリ アドレスを使用すると、新しいサブスクライバーがウェルカム メールを受信しないため、管理者がサブスクライバーにサブスクリプションが割り当てられたことを通知する必要があることに注意してください。  次の手順を実行してから、自由にメール [テンプレート](#notifying-your-subscribers-with-directory-addresses)を使ってサブスクライバーに通知し、サインイン プロセスを支援してください。

### <a name="adding-new-subscribers"></a>新しいサブスクライバーを追加する
次の手順に従って、ディレクトリ アカウントを使用して新しいサブスクライバーを追加します。

1. [ボリューム ライセンス サービス センター](https://www.microsoft.com/Licensing/servicecenter/default.aspx) (VLSC) にアクセスしてサインインします。
2. VLSC の管理ページから、**[サブスクリプション]**、**[Visual Studio サブスクリプション]** の順にクリックします。

    ![サブスクリプション メニュー](_img//vlsc/vlsc-subscriptions.png)

3. Visual Studio サブスクリプションに関連付けられている**契約番号**をクリックします。

    ![契約の選択](_img/vlsc/vlsc-agreement.png)

4. **[サブスクリプションの割り当て]** をクリックします。

    ![サブスクリプションの割り当て](_img/vlsc/vlsc-assign.png)

5. 目的の**サブスクリプション レベル**を選択します。

    ![サブスクリプション レベル](_img/vlsc/vlsc-subscription-level.png)
    
6. サブスクリプションが割り当て可能になっていることを確認し、**[次へ]** をクリックします。
7.  サブスクライバーの詳細と [電子メール アドレス] フィールドにディレクトリ アドレスを入力し、**[次へ]** をクリックします。

    ![電子メール アドレス](_img/vlsc/vlsc-email-address.png)
    
8. サブスクライバー情報を確認し、**[完了]** をクリックします。

9. 下記の[テンプレート](#notifying-your-subscribers-with-directory-addresses)を使用して、サブスクリプションがプロビジョニングされたことをサブスクライバーに通知します。

### <a name="updating-an-existing-subscriber"></a>既存のサブスクライバーを更新する
次の手順に従って、ディレクトリ アカウントを使用して既存のサブスクライバーを更新します。

1. [ボリューム ライセンス サービス センター](https://www.microsoft.com/Licensing/servicecenter/default.aspx) (VLSC) にアクセスしてサインインします。

2. VLSC の管理ページから、**[サブスクリプション]**、**[Visual Studio サブスクリプション]** の順にクリックします。

3. Visual Studio サブスクリプションに関連付けられている**契約番号**をクリックします。

4. **検索**バーで下矢印をクリックします。

5. [電子メール アドレス] フィールドを使用してサブスクライバーを検索します。

6. 結果リストからサブスクライバーの**姓**をクリックします。

7. **[編集]** をクリックします。

8. [電子メール アドレス] フィールドを目的のディレクトリ アドレスに変更し、**[保存]** をクリックします。

9. 下記のメール テンプレートを使用して、サブスクリプションがプロビジョニングされたことをサブスクライバーに通知します。

### <a name="notifying-your-subscribers-with-directory-addresses"></a>ディレクトリ アドレスを使用してサブスクライバーに通知する
ウェルカム メールがサブスクライバーに正常に送信されないため、次のメッセージをコピーして電子メールに貼り付け、サブスクライバーに送信します。 %用語% の部分を各サブスクライバーに適した情報に置き換えます。

----------- 以下をコピー (Ctrl+C) -----------

%サブスクライバー名% 様

Visual Studio サブスクリプションが割り当てられました。  Https://my.visualstudio.com にアクセスして、%ディレクトリ アドレス% アドレスを使用してログインし、サブスクリプションをアクティブ化してアクセスしてください。 

問題がある場合は、サポート チーム (https://www.visualstudio.com/subscriptions/support/) にお問い合わせください。

ページの下部で、次を選択します。
   - [Accounts, Subscriptions, and Billing Support]\(アカウント、サブスクリプション、課金サポート\)
   - [Issue]\(問題\) から、[ Subscription sign in support]\(サブスクリプションのサインイン サポート) を選択します
   - 該当する国を選択します
   - 必要なサポート オプションを選択します

----------- コピーの終了 -----------



## <a name="defining-a-work-or-school-account-as-a-personal-account"></a>職場または学校アカウントを個人用アカウントとして定義する 
「[サブスクライバーをディレクトリ アカウントに割り当てる](#assigning-subscribers-to-a-directory-account)」セクションに記載した指示に従って、新しいユーザーを追加するか、ボリューム ライセンス サービス センター (VLSC) 内でユーザーのメール アドレスを更新します。  メール アドレスがディレクトリで認識されない場合は、ユーザーがプロセスを実行して新しいアカウントを作成し、個人用アカウントとしてメール アドレスを定義する必要があります。  短期的には、Visual Studio サブスクリプション チームは、以下で定義されている ID ポリシーの免除を保証されていますが、マイクロソフトではこのポリシーを除去するために必要な機能に投資しています。

> [!WARNING]
> "職場または学校" の ID を "個人用" の ID と組み合わせることはお勧めできません。  これを行うと、組織がアカウントの所有権と制御を失い、従業員が退職後でも特定の製品やサービスに引き続きアクセスできてしまいます。  詳細については、Microsoft Identity チームのこの[ブログの記事](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/15/cleaning-up-the-azure-ad-and-microsoft-account-overlap/)を参照してください。

### <a name="defining-an-email-address-as-a-personal-account"></a>メール アドレスを個人用アカウントとして定義する
サブスクリプションがサブスクライバーに割り当てられると、サブスクライバーは、https://my.visualstudio.com にアクセスしてサブスクリプションの特典を利用するように求めるメールを受信します。  サインインしようとすると、アカウントが認識されないことを示すエラーで Visual Studio サブスクリプションのサインインが失敗します。  https://my.visualstudio.com にログインする前に、サブスクライバーに次の手順を実行するように求めます。  必要に応じて、サブスクリプションを割り当てた後、この[テンプレート](#notifying-your-subscribers-using-personal-accounts)を使用してサブスクライバーに通知できます。

1. https://my.visualstudio.com にアクセスして、**[新しい Microsoft アカウントを作成する]** をクリックします。

2. フィールドに入力します。
    - Someone@example.com ボックスにウェルカム メールを受信したメール アドレスを入力します。
    - パスワードを作成します。
    - キャンペーンの設定を選択します。
    - **[次へ]**をクリックします。

3. 検証手順を実行して、**[次へ]** をクリックします。

4. 場合によっては、新しいユーザーは、Visual Studio のプロファイルを完成させる必要があります。

5. これでサブスクリプションと特典が表示されます。

### <a name="notifying-your-subscribers-using-personal-accounts"></a>個人用アカウントを使用してサブスクライバーに通知する

上記で説明したシナリオでは、サブスクライバーは "ウェルカム メール" を受信しますが、別名定義によりサブスクライバーがサインインできない場合があります。  次のテキストを使用して、サブスクライバーに上記の手順を通知し、必要に応じてサポート オプションを勧めることができます。  %用語% の部分を各サブスクライバーに適した情報に置き換えます。

----------- 以下をコピー (Ctrl+C) -----------

%サブスクライバー名% 様

Visual Studio サブスクリプションが割り当てられ、ウェルカム メールでは、https://my.visualstudio.com にログインするように指示されています。  これは特典を使用する場合の Web サイトで、当組織では、サイトにアクセスする前に、いくつか追加手順を実行していただく必要があります。  次の指示に従って、弊社のメール アドレスに関連付けられる "Microsoft アカウント" を作成してください。  これらの手順が完了したら、ご自分のメール アドレスを使用してサブスクリプションの特典にアクセスします。
1. Visit https://my.visualstudio.com

2. 右側で [新しい Microsoft アカウントを作成する] をクリックします。

3. フォームに入力します。 
    - someone@example.com ボックスには会社のメール アドレスを使用します。
    - パスワードを入力します。
    - キャンペーンを選択します。
    - [次へ] をクリックします。

4. アカウントの検証手順を完了します。

5. 必要に応じて、Visual Studio プロファイルを完成させます。

6. これで特典が表示されます。

注: 将来、https://my.visualstudio.com にアクセスしたときに、使用するアカウント ("職場または学校アカウント" または "個人用アカウント" など) を選択するように求められる場合があります。  上記の手順を実行したら、"個人用アカウント" オプションを利用する必要があります。

問題がある場合は、サポート チーム (https://www.visualstudio.com/subscriptions/support/) にお問い合わせください。

ページの下部で、次を選択します。
   - [Accounts, Subscriptions, and Billing Support]\(アカウント、サブスクリプション、課金サポート\)
   - [Issue]\(問題\) から、[ Subscription sign in support]\(サブスクリプションのサインイン サポート) を選択します
   - 該当する国を選択します
   - 必要なサポート オプションを選択します

----------- コピーの終了 -----------