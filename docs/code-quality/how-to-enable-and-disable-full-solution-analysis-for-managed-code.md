---
title: '方法: を有効にして、マネージ コードの完全なソリューション分析を無効にする |Microsoft ドキュメント'
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 4c5985792138d334de103523478841917555fc56
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>方法: を有効にして、マネージ コードの完全なソリューション分析を無効にします。

*完全ソリューション解析*は、ソリューション内の開いている Visual c# または Visual Basic ファイルでのみコード分析の問題が発生することができますをもコードでファイルを Visual Studio 機能は閉じられます。 完全ソリューション解析は、既定では、*有効になっている*Visual basic の場合と*無効になっている*Visual c# の場合。

すべてのファイルにすべての問題が発生すると便利であることができますが、無駄なこともできます。 長くなる Visual Studio ソリューションが非常に大きいまたは多くのファイルが含まれる場合。 表示の問題の数を制限して、Visual Studio のパフォーマンスを向上させる、完全なソリューション分析を無効にできます。 必要に応じて簡単に、この機能を再有効化することができます。

## <a name="to-toggle-full-solution-analysis"></a>完全なソリューション分析を切り替える

1. 開くには、**オプション**ダイアログ ボックスで、Visual Studio のメニュー バーで選択**ツール** > **オプション**です。

1. **オプション** ダイアログ ボックスで、選択**テキスト エディター** > **c#**または**基本** >  **高度な**します。

1. 選択、**完全ソリューション解析を有効にする**完全なソリューション分析を有効または無効にするボックスをオフにする チェック ボックスです。 選択**OK**終了するとします。

    ![完全なソリューション分析 チェック ボックスを有効にします。](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>結果を有効にして、完全なソリューション分析を無効にします。

次のスクリーン ショットでは、完全なソリューション分析を有効にすると、結果を確認できます。 すべてのエラーとコード分析の問題で*すべて*ソリューション内のファイルの表示、かどうか、ファイルが開いているかに関係なく。

![完全ソリューション解析を有効にします。](../code-quality/media/fsa_enabled.png)

次のスクリーン ショットは、完全なソリューション分析を無効にした後、同じソリューションからの結果を示します。 エラーと開いているソリューション ファイルでコード分析の問題のみに表示されます、**エラー一覧**です。

![完全ソリューション解析を無効になっています。](../code-quality/media/fsa_disabled.png)

## <a name="automatically-disable-full-solution-analysis"></a>完全なソリューション分析を自動的に無効にします。

Visual Studio を検出する場合は、200 MB または少ないシステム メモリに使用できる場合に自動的に無効に完全なソリューション分析 (およびその他のいくつかの機能) が有効な場合です。 このような場合は、Visual Studio が一部の機能を無効になっていることを通知するアラートが表示されます。 ボタンを使用する場合は、完全なソリューション分析を再度有効にすることができます。

![完全ソリューション解析を中断する警告テキスト](../code-quality/media/fsa_alert.png)