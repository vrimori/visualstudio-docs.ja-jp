---
title: '方法: Visual Studio での ASP.NET Web アプリケーションのコード分析を構成します。'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: c924a866f1bb34f41664fbf62e372b77f4d2620e
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178238"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>方法: ASP.NET Web アプリケーション用にコード分析を構成する

Visual Studio では、コード分析の一覧から選択できる*ルール セット*に適用する[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]web アプリケーション。 既定の規則セットは Microsoft 最小推奨規則です。 Web サイトに適用する別のルールを選択できます。

1. Web サイトを選択します。**ソリューション エクスプ ローラー**します。

2. **分析** メニューのをクリックして**Web サイトのコード分析を構成する**します。

3. ソリューションを選択し、ソリューションが 1 つ以上のプロジェクト場合、からビルド構成とターゲットのオペレーティング システムを選択、**構成**と**プラットフォーム**を一覧表示します。

4. ソリューション内の各プロジェクトをクリックして、**ルール セットの**列、および実行するルールの名前を設定 をクリックします。

5. 既定では、ソリューション内のすべてのプロジェクトでコード分析を実行します。 無効にするか、または特定のプロジェクトのコード分析を有効にして、これらの手順に従います。

    1. プロジェクト名を右クリックし、[プロパティ] をクリックします。

    2. オンまたはオフ、**コード分析の有効化**チェック ボックスをオンします。 手動では選択してもコード分析を実行することができます**Web サイトでコード分析を実行**から、**分析**メニュー。

6. **この規則セットを実行**ドロップダウン リストで、これらの手順に従います。

    - 使用する規則セットを選択します。

    - 選択**\<参照 >** を既存のカスタム規則セットを指定されていないリスト。

    - 定義、[カスタム規則セット](../code-quality/how-to-create-a-custom-rule-set.md)します。