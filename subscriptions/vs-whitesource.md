---
title: WhiteSource Bolt 特典 | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 12/19/2018
ms.topic: Get-Started-Article
description: Visual Studio サブスクリプションに含まれる WhiteSource Bolt サブスクリプションをアクティブ化する方法を説明します。
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: d9f4db463dad3ee2fbb216284791018dc504d7b6
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2018
ms.locfileid: "53739985"
---
#  <a name="whitesource-bolt-in-visual-studio-subscriptions"></a>Visual Studio サブスクリプションの WhiteSource Bolt

オープン ソースの脆弱性を見つけ出して修正し、使用しているビルドのすべてのオープン ソース コンポーネントに関する包括的なインベントリとライセンスのレポートを作成します。 一部のサブスクリプションには、6 か月間の無料アクセスが含まれています。

## <a name="activation-steps"></a>アクティブ化の手順

1. WhiteSource Bolt 特典をアクティブ化するには、[https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs) にサインインします。

2. [ツール] セクションで、 WhiteSource Bolt のタイルを見つけて、特典タイルの下部にある **[コードを取得]** リンクをクリックします。
   > [!div class="mx-imgBorder"]
   > ![WhiteSource 特典タイル](_img/vs-whitesource/vs-whitesource-tile.png)

3. アクティブ化コードを表示する通知を受け取ります。  **コードをクリップボードにコピーし**、**[アクティブ化]** をクリックします。
   > [!div class="mx-imgBorder"]
   > ![WhiteSource 特典コード](_img/vs-whitesource/vs-whitesource-code.png)

4. WhiteSource の Web ページで、**[Activate]\(アクティブ化\)** ボタンをクリックするか、ページの **[Activate your account]\(アカウントのアクティブ化\)** セクションまで下にスクロールします。
   > [!div class="mx-imgBorder"]
   > ![WhiteSource 特典のアクティブ化](_img/vs-whitesource/vs-whitesource-activate-page-cropped.png)

5. ページの **[Activate your account]\(アカウントのアクティブ化\)** セクションでは、4 つのステップが案内されます。

   - Microsoft Visual Studio Marketplace から WhiteSource Bolt 拡張機能を[インストール](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt)します。 拡張機能をインストールする権限がない場合は、「[Install free extensions for Azure DevOps Services](/azure/devops/marketplace/install-vsts-extension?view=vsts)」 (Azure DevOps Services の拡張機能を無料でインストールする) を参照してください。


~~~
Click the green **Install** button if you are using Azure DevOps Services, or the **Download** button for Team Foundation Server.  For this example, we will use Azure DevOps Services.
> [!div class="mx-imgBorder"]
> ![WhiteSource Benefit Install Extension](_img\vs-whitesource\vs-whitesource-download-install.png)

- Next, select the Azure DevOps organization you want to use and click **Confirm**.  (If you have not yet set up Azure DevOps Services, visit the [Benefits](https://my.visualstudio.com/benefits) page and activate your Azure DevOps Services benefit.)

> [!div class="mx-imgBorder"]
> ![WhiteSource Benefit Confirm Account](_img\vs-whitesource\vs-whitesource-confirm-account.png)

- You’ll receive a confirmation that the extension is installed and ready to use.  Click **Get started** to return to the WhiteSource Bolt page and continue.
> [!div class="mx-imgBorder"]
> ![WhiteSource Benefit Install Complete](_img\vs-whitesource\vs-whitesource-install-complete.png)
~~~

5. Azure DevOps プロジェクトのダッシュボードを開き、**Azure Pipelines** メニューをクリックして **WhiteSource Bolt** を選択します。
   > [!div class="mx-imgBorder"]
   > ![WhiteSource 特典拡張機能の追加](_img/vs-whitesource/vs-whitesource-installed-cropped.png)

6. WhiteSource Bolt 特典タイルからアクティブ化コードを貼り付けて、**[アクティブ化]** をクリックします。 各アクティブ化コードでアクティブ化できるプロジェクトは 1 つだけです。
   > [!div class="mx-imgBorder"]
   > ![WhiteSource 特典アクティブ化コード](_img/vs-whitesource/vs-whitesource-activate-code-cropped.png)

7. アクティブ化が完了し、180 日間サブスクリプションに残っています。

8. ビルド ステップの 1 つとして、WhiteSource Bolt 拡張機能を追加する必要があります。  方法については、[WhiteSource Bolt ページ](https://www.whitesourcesoftware.com/whitesource_bolt_visualstudio_2017/#activate)のビデオをご覧ください。

9. ビルドを実行すると、次の包括的なレポートとダッシュボードが自動的に生成されます。
    - セキュリティ脆弱性ダッシュボード
    - セキュリティ脆弱性レポート
    - 古いライブラリ レポート
    - ライセンス リスクとコンプライアンス ダッシュボード
    - インベントリ レポート

## <a name="eligibility"></a>特典を受ける条件

| サブスクリプション レベル                                                 |     チャネル                                            | 特長                                                          | 更新可能かどうか    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Standard)   | VL、Azure、リテール、一部の NFR<sup>1</sup> | 6 か月       |  はい          |
| Visual Studio Professional (Standard) | VL、Azure、リテール                                       | 使用できません。                                                           |N/A         |
| Visual Studio Test Professional (標準)                         | VL、リテール                                              | 使用できません                                             |  N/A         |
| MSDN Platforms (標準)                                          | VL、リテール                                              | 使用できません                                              | N/A         |
| Visual Studio Dev Essentials | N/A  | 使用できません |N/A |
| Visual Studio Enterprise、Visual Studio Professional (月間クラウド) | Azure                                       | 使用できません                                                           |N/A|

<sup>1</sup>  *Microsoft Partner Network (Enterprise) が含まれます。他の Not for Resale (NFR)、Visual Studio Industry Partner (VSIP)、FTE、MCT Software & Services Developer、BizSpark、Imagine、Microsoft Valued Professional (MVP)、Region Director (RD)、MCT Software & Services、Microsoft Partner Network (Professional) は含まれません。*


> [!NOTE]
> Microsoft では、クラウド サブスクリプションの Visual Studio Professional 年間サブスクリプションおよび Visual Studio Enterprise 年間サブスクリプションが提供されなくなりました。 サブスクリプションの更新、増減、キャンセルに関する既存のお客様のエクスペリエンスと機能については変更はありません。 新規のお客様は、[https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) に移動し、Visual Studio のさまざまな購入オプションを調べることをお勧めします。


どのサブスクリプション使用しているかわからない場合は次の手順を実行してください。  [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) に接続し、お使いのメール アドレスに割り当てられているすべてのサブスクリプションを確認します。 すべてのサブスクリプションが表示されない場合は、1 つ以上のサブスクリプションが別のメール アドレスに割り当てられている可能性があります。  それらのサブスクリプションを表示するには、そのメール アドレスを使用してサインインする必要があります。

## <a name="support-resources"></a>サポート リソース

-  WhiteSource Bolt のヘルプが必要ですか。  [https://www.whitesourcesoftware.com/vse_whitesource_bolt/](https://www.whitesourcesoftware.com/vse_whitesource_bolt/) で WhiteSource Bolt の担当者とオンライン チャットしてください。
-  Visual Studio サブスクリプションの販売、サブスクリプション、アカウント、課金のサポートについては、Visual Studio [サブスクリプション サポート](https://visualstudio.microsoft.com/subscriptions/support/)にお問い合わせください。
-  Visual Studio IDE、Azure DevOps Services、またはその他の Visual Studio の製品やサービスに関する質問がありますか。  [Visual Studio のサポート](https://visualstudio.microsoft.com/support/)にアクセスしてください。