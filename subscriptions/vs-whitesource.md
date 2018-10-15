---
title: WhiteSource Bolt 特典 | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/11/2017
ms.topic: Get-Started-Article
description: Visual Studio サブスクリプションに含まれる WhiteSource Bolt サブスクリプションをアクティブ化する方法を説明します。
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: a7c384a8bc4b84aea4982bd195b0d92820c68ecb
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542352"
---
#  <a name="whitesource-bolt-in-visual-studio-subscriptions"></a>Visual Studio サブスクリプションの WhiteSource Bolt

オープン ソースの脆弱性を見つけ出して修正し、使用しているビルドのすべてのオープン ソース コンポーネントに関する包括的なインベントリとライセンスのレポートを作成します。 一部のサブスクリプションには、6 か月間の無料アクセスが含まれています。

## <a name="activation-steps"></a>アクティブ化の手順

1.  WhiteSource Bolt 特典をアクティブ化するには、[https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs) にサインインします。

2.  [ツール] セクションで、 WhiteSource Bolt のタイルを見つけて、特典タイルの下部にある **[コードを取得]** リンクをクリックします。
    > [!div class="mx-imgBorder"]
    > ![WhiteSource 特典タイル](_img\vs-whitesource\vs-whitesource-tile.png)

2.  アクティブ化コードを表示する通知を受け取ります。  **コードをクリップボードにコピーし**、**[アクティブ化]** をクリックします。
    > [!div class="mx-imgBorder"]
    > ![WhiteSource 特典コード](_img\vs-whitesource\vs-whitesource-code.png)

3.  WhiteSource の Web ページで、**[Activate]\(アクティブ化\)** ボタンをクリックするか、ページの **[Activate your account]\(アカウントのアクティブ化\)** セクションまで下にスクロールします。
    > [!div class="mx-imgBorder"]
    > ![WhiteSource 特典のアクティブ化](_img\vs-whitesource\vs-whitesource-activate-page-cropped.png)

4.  ページの **[Activate your account]\(アカウントのアクティブ化\)** セクションでは、4 つのステップが案内されます。

    - Microsoft Visual Studio Marketplace から WhiteSource Bolt 拡張機能を[インストール](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt)します。 拡張機能をインストールする権限がない場合は、「[Install free extensions for Azure DevOps Services](/azure/devops/marketplace/install-vsts-extension?view=vsts)」 (Azure DevOps Services の拡張機能を無料でインストールする) を参照してください。


    Azure DevOps Services を使っている場合は緑の **[インストール]** ボタンをクリックし、Team Foundation Server の場合は **[ダウンロード]** ボタンをクリックします。  この例では、Azure DevOps Services を使用します。
    > [!div class="mx-imgBorder"]
    > ![WhiteSource 特典拡張機能のインストール](_img\vs-whitesource\vs-whitesource-download-install.png)

    - 次に、使用する Azure DevOps 組織を選択して、**[確認]** をクリックします。  (まだ Azure DevOps Services を設定していない場合は、[特典](https://my.visualstudio.com/benefits)ページに移動して Azure DevOps Services 特典をアクティブ化します。)

    > [!div class="mx-imgBorder"]
    > ![WhiteSource 特典アカウントの確認](_img\vs-whitesource\vs-whitesource-confirm-account.png)

    - 拡張機能がインストールされて使えることを示す確認が表示されます。  **[Get started]\(使用開始\)** をクリックして WhiteSource Bolt ページに戻って続けます。
    > [!div class="mx-imgBorder"]
    > ![WhiteSource 特典インストール完了](_img\vs-whitesource\vs-whitesource-install-complete.png)

5.  Azure DevOps プロジェクトのダッシュボードを開き、**Azure Pipelines** メニューをクリックして **WhiteSource Bolt** を選択します。
    > [!div class="mx-imgBorder"]
    > ![WhiteSource 特典拡張機能の追加](_img\vs-whitesource\vs-whitesource-installed-cropped.png)

6. WhiteSource Bolt 特典タイルからアクティブ化コードを貼り付けて、**[アクティブ化]** をクリックします。 各アクティブ化コードでアクティブ化できるプロジェクトは 1 つだけです。
    > [!div class="mx-imgBorder"]
    > ![WhiteSource 特典アクティブ化コード](_img\vs-whitesource\vs-whitesource-activate-code-cropped.png)

7.  アクティブ化が完了し、180 日間サブスクリプションに残っています。

8.  ビルド ステップの 1 つとして、WhiteSource Bolt 拡張機能を追加する必要があります。  方法については、[WhiteSource Bolt ページ](https://www.whitesourcesoftware.com/whitesource_bolt_visualstudio_2017/#activate)のビデオをご覧ください。

9. ビルドを実行すると、次の包括的なレポートとダッシュボードが自動的に生成されます。
    - セキュリティ脆弱性ダッシュボード
    - セキュリティ脆弱性レポート
    - 古いライブラリ レポート
    - ライセンス リスクとコンプライアンス ダッシュボード
    - インベントリ レポート

## <a name="eligibility"></a>特典を受ける条件

| サブスクリプション レベル                                                 |     チャネル                                            | 特長                                                          | 更新可能かどうか    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (標準、年間クラウド)   | VL、Azure、リテール、一部の NFR<sup>1</sup> | 6 か月       |  [はい]          |
| Visual Studio Professional (標準、年間クラウド) | VL、Azure、リテール                                       | 使用できません。                                                           |N/A         |
| Visual Studio Test Professional (標準)                         | VL、リテール                                              | 使用できません                                             |  N/A         |
| MSDN Platforms (標準)                                          | VL、リテール                                              | 使用できません                                              | N/A         |
| Visual Studio Dev Essentials | N/A  | 使用できません |N/A |
| Visual Studio Enterprise、Visual Studio Professional (月間クラウド) | Azure                                       | 使用できません                                                           |N/A|

<sup>1</sup> *Microsoft Partner Network (Enterprise) が含まれます。他の Not for Resale (NFR)、Visual Studio Industry Partner (VSIP)、FTE、MCT Software & Services Developer、BizSpark、Imagine、Microsoft Valued Partner (MVP)、Region Director (RD)、MCT Software & Services、Microsoft Partner Network (Professional) は含まれません。*

どのサブスクリプション使用しているかわからない場合は次の手順を実行してください。  [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) に接続し、お使いのメール アドレスに割り当てられているすべてのサブスクリプションを確認します。 すべてのサブスクリプションが表示されない場合は、1 つ以上のサブスクリプションが別のメール アドレスに割り当てられている可能性があります。  それらのサブスクリプションを表示するには、そのメール アドレスを使用してサインインする必要があります。

## <a name="support-resources"></a>サポート リソース

-  WhiteSource Bolt のヘルプが必要ですか。  https://www.whitesourcesoftware.com/vse_whitesource_bolt/ で WhiteSource Bolt の担当者とオンライン チャットしてください。
-  Visual Studio サブスクリプションの販売、サブスクリプション、アカウント、課金のサポートについては、Visual Studio [サブスクリプション サポート](https://visualstudio.microsoft.com/subscriptions/support/)にお問い合わせください。
-  Visual Studio IDE、Azure DevOps Services、またはその他の Visual Studio の製品やサービスに関する質問がありますか。  [Visual Studio のサポート](https://visualstudio.microsoft.com/support/)にアクセスしてください。