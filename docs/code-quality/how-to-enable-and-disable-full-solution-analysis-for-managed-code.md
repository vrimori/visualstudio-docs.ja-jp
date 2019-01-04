---
title: '方法: 有効にして、マネージ コードの完全ソリューション解析を無効にします。'
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- dotnet
ms.openlocfilehash: b6e5d73f0a08511730cb79eccf60570bad804137
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53937885"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>方法: 有効にして、マネージ コードの完全なソリューション分析を無効にします。

*完全ソリューション解析*が開いている Visual c# または Visual Basic ファイル、ソリューション内でのみコード分析の問題が発生することができますをもコードでファイルを Visual Studio の機能は閉じられます。 完全ソリューション解析は、既定では、*有効になっている*Visual basic の場合と*無効になっている*Visual c# 用です。

すべてのファイルですべての問題が発生すると便利であることができますが、注意をそらすこともできます。 長くなる Visual Studio ソリューションが非常に大きいか、含まれるファイルの場合。 示されている問題の数を制限し、Visual Studio のパフォーマンスを向上させる、完全ソリューション解析を無効にすることができます。 必要に応じて簡単に、この機能を再有効化することができます。

## <a name="to-toggle-full-solution-analysis"></a>完全ソリューション解析を切り替える

1. 開くには、**オプション** ダイアログ ボックスで、Visual Studio でメニュー バーで選択**ツール** > **オプション**します。

1. **オプション** ダイアログ ボックスで、選択**テキスト エディター** > **c#** または**基本的な** >  **高度な**します。

1. 選択、**完全ソリューション解析を有効にする**チェック ボックスを完全なソリューション分析を有効または無効にするボックスをオフにします。 選択**OK**完了したら。

    ![完全なソリューション分析 チェック ボックスを有効にします。](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>結果を有効にして、完全ソリューション解析を無効にします。

次のスクリーン ショットでは、完全ソリューション解析を有効にすると、結果を確認できます。 すべてのエラーとコード分析の問題で*すべて*ソリューション内のファイルの表示、かどうか、開いているファイルかどうかに関係なく。

![完全ソリューション解析を有効にします。](../code-quality/media/fsa_enabled.png)

次のスクリーン ショットでは、完全ソリューション解析を無効にした後、同じソリューションから結果を示しています。 エラーと開いているソリューション ファイルでコード分析の問題のみに表示される、**エラー一覧**します。

![完全ソリューション解析を無効になっています。](../code-quality/media/fsa_disabled.png)

## <a name="automatically-disable-full-solution-analysis"></a>完全ソリューション解析を自動的に無効にします。

Visual Studio を検出する場合は 200 MB またはシステム メモリの利用可能になりますが、自動的に無効になります完全ソリューション解析 (およびその他のいくつかの機能) が有効になっている場合。 このような場合は、Visual Studio が一部の機能を無効になっていることを通知するアラートが表示されます。 ボタンには、する場合は、完全なソリューション分析を再度有効にすることができます。

![完全ソリューション解析を中断する警告テキスト](../code-quality/media/fsa_alert.png)