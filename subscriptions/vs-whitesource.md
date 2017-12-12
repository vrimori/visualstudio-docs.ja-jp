---
title: "WhiteSource Bolt 特典"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: "Visual Studio サブスクリプションに含まれる WhiteSource Bolt サブスクリプションをアクティブ化する方法を説明します。"
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: c1976d9eaa6ef18978a9e9d5453c3080741223d5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
#  <a name="activating-the-whitesource-bolt-benefit-in-visual-studio-subscriptions"></a>Visual Studio サブスクリプションの WhiteSource Bolt 特典をアクティブ化する

オープン ソースの脆弱性を見つけ出して修正し、使用しているビルドのすべてのオープン ソース コンポーネントに関する包括的なインベントリとライセンスのレポートを作成します。  Enterprise サブスクリプションには、6 か月間有効な無料サブスクリプションが含まれます。 

1.  WhiteSource Bolt 特典を使うには、特典タイルの下部にある **[コードの取得]** リンクをクリックします。    

![WhiteSource 特典タイル](_img\vs-whitesource\vs-whitesource-tile.png)

2.  アクティブ化コードを表示する通知を受け取ります。  **コードをクリップボードにコピーし**、**[アクティブ化]** をクリックします。 

![WhiteSource 特典コード ](_img\vs-whitesource\vs-whitesource-code.png)

3.  WhiteSource の Web ページで、**[Activate]\(アクティブ化\)** ボタンをクリックするか、ページの **[Activate your account]\(アカウントのアクティブ化\)** セクションまで下にスクロールします。  

![WhiteSource 特典のアクティブ化](_img\vs-whitesource\vs-whitesource-activate-page-cropped.png)

4.  ページの **[Activate your account]\(アカウントのアクティブ化\)** セクションでは、4 つのステップが案内されます。
- Microsoft Visual Studio Marketplace から WhiteSource Bolt 拡張機能を[インストール](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt)します。 拡張機能をインストールするアクセス許可がない場合は、[こちらのページ](https://www.visualstudio.com/en-us/docs/marketplace/get-vsts-extensions#request)をご覧ください。

    VSTS を使っている場合は緑の **[Install]\(インストール\)** ボタンをクリックし、Team Foundation Server の場合は **[Download]\(ダウンロード\)** ボタンをクリックします。  この例では、VSTS を使います。 

![WhiteSource 特典拡張機能のインストール](_img\vs-whitesource\vs-whitesource-download-install.png)

- 次に、使う VSTS アカウントを選び、**[Confirm]\(確認\)** をクリックします   (VSTS をまだセットアップしていない場合は、[[特典]](https://my.visualstudio.com/benefits) ページで VSTS 特典をアクティブ化します)。

![WhiteSource 特典アカウントの確認](_img\vs-whitesource\vs-whitesource-confirm-account.png)

- 拡張機能がインストールされて使えることを示す確認が表示されます。  **[Get started]\(使用開始\)** をクリックして WhiteSource Bolt ページに戻って続けます。  

![WhiteSource 特典インストール完了](_img\vs-whitesource\vs-whitesource-install-complete.png)

5.  Visual Studio Team Services (VSTS) プロジェクト ダッシュボードを開き、**[ビルドとリリース]** メニューをクリックして、**[WhiteSource Bolt]** を選びます。

![WhiteSource 特典拡張機能の追加](_img\vs-whitesource\vs-whitesource-installed-cropped.png)

6. WhiteSource Bolt 特典タイルからアクティブ化コードを貼り付けて、**[アクティブ化]** をクリックします。 各アクティブ化コードでアクティブ化できるプロジェクトは 1 つだけです。 

![WhiteSource 特典アクティブ化コード](_img\vs-whitesource\vs-whitesource-activate-code-cropped.png)

7.  アクティブ化が完了し、180 日間サブスクリプションに残っています。 
8.  ビルド ステップの 1 つとして、WhiteSource Bolt 拡張機能を追加する必要があります。  方法については、[WhiteSource Bolt ページ](https://www.whitesourcesoftware.com/whitesource_bolt_visualstudio_2017/#activate)のビデオをご覧ください。  
9. ビルドを実行すると、次の包括的なレポートとダッシュボードが自動的に生成されます。
- セキュリティ脆弱性ダッシュボード
- セキュリティ脆弱性レポート
- 古いライブラリ レポート
- ライセンス リスクとコンプライアンス ダッシュボード
- インベントリ レポート
