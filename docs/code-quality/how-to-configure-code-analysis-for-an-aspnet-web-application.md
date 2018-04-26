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
ms.openlocfilehash: bb1adaf9e97a950c6e9c53b3734debf5588fe0b9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>方法: ASP.NET Web アプリケーション用にコード分析を構成する

Visual Studio では、コード分析の一覧から選択できる*ルール セット*に適用する[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Web アプリケーションです。 既定の規則セットは Microsoft 最小推奨規則です。 Web サイトに適用する別のルールを選択することができます。

1. Web サイトを選択して**ソリューション エクスプ ローラー**です。

2. **分析** メニューのをクリックして**Web サイトのコード分析を構成する**です。

3. ソリューションを選択し、このソリューションに複数のプロジェクトは場合からのビルドの構成とターゲットのオペレーティング システムを選択して、**構成**と**プラットフォーム**を一覧表示します。

4. ソリューション内の各プロジェクトをクリックして、**ルール セット**列、および実行するセットのルールの名前をクリックします。

5. 既定では、ソリューション内のすべてのプロジェクトでコード分析を実行します。 特定のプロジェクトのコード分析を有効または無効に、これらの手順に従います。

    1. プロジェクト名を右クリックし、[プロパティ] をクリックします。

    2. オンまたはオフ、**コード分析の有効化**チェック ボックスをオンします。 手動では選択してもコード分析を実行することができます**Web サイトでコード分析を実行**から、**分析**メニュー。

6. **この規則セットを実行**ドロップダウン リストで、これらの手順に従います。

    - 使用する規則セットを選択します。

    - 選択**\<参照 >** 既存のカスタム規則セットを指定ではありません、ボックスの一覧です。

    - 定義、[カスタム規則セット](../code-quality/how-to-create-a-custom-rule-set.md)です。