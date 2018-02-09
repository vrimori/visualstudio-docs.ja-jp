---
title: "Visual Studio サブスクライバー向けの VSTS | Microsoft Docs"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: Understand how you can use Visual Studio Team Services (VSTS) as a Visual Studio subscriber.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: d3287740daded32afa9b93e109a76b1804e82a75
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2018
---
# <a name="visual-studio-team-services-vsts-benefit-in-visual-studio-subscriptions"></a>Visual Studio サブスクリプションの Visual Studio Team Services (VSTS) 特典

## <a name="overview"></a>概要 
あらゆる言語を対象とした、無料の Git リポジトリ、アジャイル計画ツール、ホスト型ビルド。お使いの IDE を補完します。 
- チームにとって最適な開発環境を作る 
- アイデアからリリースまで常につながり続ける 
- コードの品質を向上させて、早期に問題を把握する
- Azure の配置を自動化して容易にする
- 強力な機能によって生産性を高める 

## <a name="eligibility"></a>特典を受ける条件
| サブスクリプション レベル/プログラム                                                  | 特長               | 更新可能かどうか                                                         |
|-------------------------------------------------------------------------------|-----------------------|--------------------------------------------------------------------|
| Visual Studio Enterprise Standard                                             | 上級アクセス       |  [はい]                                                               |
| Visual Studio Enterprise - 年間プラン                                               | 上級アクセス       |  [はい]                                                               |
| Visual Studio Enterprise - 月間プラン                                              | 上級アクセス       |  [はい]                                                               |
| Visual Studio Professional Standard                                           | 基本アクセス          |  [はい]                                                               |
| Visual Studio Professional - 年間プラン                                             | 基本アクセス          |  [はい]                                                               | 
| Visual Studio Professional - 月間プラン                                            | 基本アクセス          |  [はい]                                                               |
| Visual Studio Test Pro                                                        | 上級アクセス       |  [はい]                                                               |
| MSDN Platforms                                                                | 上級アクセス       |  [はい]                                                               |
| Visual Studio Dev Essentials                                                  | 利害関係者           |  [はい]                                                               |
| Visual Studio Enterprise - NFR<sup>1</sup>                                               | 上級アクセス       |  [はい]                                                               |
| Visual Studio Enterprise - FTE                                                | 上級アクセス       |  [はい]                                                               |
| Visual Studio Enterprise - Microsoft Partner Network                          | 上級アクセス       |  [はい]                                                               |
| Visual Studio Professional - Microsoft Partner Network                        | 基本アクセス          |  [はい]                                                               |
| Visual Studio Enterprise – Imagine (Standard)                                 | 基本アクセス          |  [はい]                                                               |
| Visual Studio Enterprise – Imagine (Premium)                                  | 基本アクセス          |  [はい]                                                               |
| Visual Studio Enterprise – BizSpark                                           | 上級アクセス       |  [はい]                                                               |
| マイクロソフト認定トレーナー - Software & Services                             | 基本アクセス          |  [はい]                                                               |
| マイクロソフト認定トレーナー - Software & Services Developer                   | 上級アクセス       |  [はい]                                                               |

<sup>1</sup>  *Not for Resale (NFR)、Microsoft Valued Partner (MVP)、Region Director (RD)、Visual Studio Industry Partner (VSIP) が含まれます。*  

どのサブスクリプション使用しているかわからない場合は次の手順を実行してください。  [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) に接続し、電子メール アドレスに割り当てられているすべてのサブスクリプションを表示します。 すべてのサブスクリプションが表示されない場合は、1 つ以上のサブスクリプションが別のメール アドレスに割り当てられている可能性があります。  それらのサブスクリプションを表示するには、そのメール アドレスを使用してサインインする必要があります。 

Visual Studio サブスクリプションのアクティブ化に使ったものと同じ ID を使って VSTS にサインインすると、そのことが自動的に認識されます。 これは、サブスクライバー ポータルにログインするときに使うプライマリ ID と、Visual Studio サブスクリプションに構成した代替 ID の両方に対して機能します。 VSTS は、Microsoft アカウント (@outlook.com など) と職場または学校アカウント (組織で管理されている Azure Active Directory を使います) の両方をサポートしています。 プライマリ ID と代替 ID の両方を VSTS で使うことができ、任意の数の VSTS アカウントにメンバーとして参加することができます。

VSTS を使うには、アカウントが必要です。 既存のアカウントでサインインすることも、新しく作成することもできます。  新しいアカウントを作成するには:
1.  [https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs) にサインインします。
2.  [ツール] セクションで、 Visual Studio Team Services のタイルを見つけて、特典タイルの下部にある [開始する] リンクをクリックします。   

各サブスクリプションには次の VSTS 機能が含まれます。 
- Visual Studio Enterprise: [Basic](https://www.visualstudio.com/team-services/compare-features/)、[Test Manager](https://marketplace.visualstudio.com/items?itemName=ms.vss-testmanager-web)、[Package Management](https://marketplace.visualstudio.com/items?itemName=ms.feed)
- Visual Studio Professional: [Basic](https://www.visualstudio.com/team-services/compare-features/)
- MSDN Platforms: [Basic](https://www.visualstudio.com/team-services/compare-features/)、[Test Manager](https://marketplace.visualstudio.com/items?itemName=ms.vss-testmanager-web)
- Visual Studio Test Professional: [Basic](https://www.visualstudio.com/team-services/compare-features/)、[Test Manager](https://marketplace.visualstudio.com/items?itemName=ms.vss-testmanager-web)

3.  VSTS プロジェクト サイトの名前を入力します。  

4.  プロジェクト管理に **Git** または **Team Foundation バージョン管理 (TFVC)** のどちらを使うかを選びます。  この選択は、作成するチーム プロジェクトごとに永続的に適用されますが、同じチーム プロジェクト コレクションで TFVC と Git の両方のチーム プロジェクトを使用できます。  どちらを使えばよいかわからない場合は以下を参考にしてください。 
    - Git: Git は分散型のバージョン管理システムです。 それぞれの開発者は、自分の開発用コンピューターにソース リポジトリ全体のコピーを保持します。 開発者は、ネットワーク接続がなくても開発用コンピューター上で変更セットをコミットし、履歴の表示や比較などのバージョン管理操作を実行できます。  Git について詳しくは、[こちらをご覧ください](https://www.visualstudio.com/docs/git/gitquickstart)
    - TFVC: Team Foundation バージョン管理 (TFVC) は、一元化されたバージョン管理システムです。 通常、チーム メンバーの開発用コンピューターには、各ファイルの 1 つのバージョンだけが存在します。 履歴データはサーバーにのみ保持されます。 分岐はパスに基づき、サーバー上で作成されます。 Team Foundation バージョン管理の詳細については、[こちら](https://www.visualstudio.com/docs/tfvc/overview)を参照してください。

 
5.  プロジェクト名、作業の編成方法 (アジャイル、スクラム、CMMI)、プロジェクトをホストする場所、作業の共有方法などのオプションをカスタマイズするには、**[詳細の変更]** をクリックします。  [続行] をクリックします。

# <a name="create-your-vsts-account"></a>VSTS アカウントを作成する

6.  アカウントの作成にはしばらくかかります。その後、初めてのプロジェクトの VSTS ページが表示されます。指定した名前が使われています。  Visual Studio Team Services を使い始める準備ができました。

アカウント作成成功を確認するメールも受け取ります。  また、アカウント URL およびサインインと優先のメール アドレスも一覧表示されます。  

![VSTS 特典ウェルカム メール](_img\vs-vsts\vs-vsts-welcome.png)


## <a name="faq"></a>FAQ
### <a name="q--what-is-the-difference-between-free-basic-access-and-advanced-access"></a>Q: 無料、基本アクセス、上級アクセスの違いは何ですか。
A: 使用できる機能はアクセス レベルによって異なります。  [アクセス レベル](/vsts/security/access-levels)に関する詳細情報を確認してください。 

### <a name="q--how-do-i-add-users-to-my-vsts-account-or-team-project"></a>Q: VSTS アカウントまたはチーム プロジェクトにユーザーを追加するにはどうすればよいですか。
A: VSTS で[ユーザーとアクセスを管理する方法](/vsts/accounts/add-account-users-from-user-hub)を学習してください。

## <a name="support-resources"></a>サポート リソース
-  Visual Studio サブスクリプションの販売、サブスクリプション、アカウント、課金のサポートについては、Visual Studio [サブスクリプション サポート](https://www.visualstudio.com/subscriptions/support/)にお問い合わせください。
-  Visual Studio IDE、Visual Studio Team Services、またはその他の Visual Studio の製品やサービスに関する質問がありますか。  [Visual Studio のサポート](https://www.visualstudio.com/support/)にアクセスしてください。 
-  完全な Visual Studio Team Services のドキュメントについては、/vsts/ を参照してください。
VSTS を使うには、アカウントを作成するか、他のユーザーが所有するアカウントのメンバーとして追加される必要があります。 VSTS アカウントの作成は無料であり、複数の VSTS アカウントを作成することができます。 

[VSTS にサインアップする方法](/vsts/accounts/index)
