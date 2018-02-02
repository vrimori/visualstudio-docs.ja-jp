---
title: "方法: を有効にして、マネージ コードの完全なソリューション分析を無効にする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 64b541093aaf1a710976c0f53a3214b5d2a47e0d
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>方法: を有効にして、マネージ コードの完全なソリューション分析を無効にします。

*完全ソリューション解析*は、ソリューション内の開いている Visual c# または Visual Basic ファイルでのみコード分析の問題が発生することができますをもコードでファイルを Visual Studio 機能は閉じられます。 既定では、完全なソリューション分析は、Visual Basic および無効になっている Visual c# 可能です。

すべてのファイル内のすべての問題を確認できるものは役立ちますが、無駄なことがあります。 ことも低速の Visual Studio ダウン場合は、ソリューションが非常に大きいか、多くのファイルです。 表示の問題の数を制限して、Visual Studio のパフォーマンスを向上させる、完全なソリューション分析を無効にできます。 必要に応じて簡単に、この機能を再有効化することができます。

## <a name="to-toggle-full-solution-analysis"></a>完全なソリューション分析を切り替える

1. 開くには、**オプション**ダイアログ ボックスで、Visual Studio のメニュー バーで選択**ツール** > **オプション**です。

1. **オプション** ダイアログ ボックスで、選択**テキスト エディター** > **c#**または**基本** >  **高度な**します。

1. 選択、**完全ソリューション解析を有効にする**完全なソリューション分析を有効または無効にするボックスをオフにする チェック ボックスです。 選択、 **OK**終わったときにボタンをクリックします。

    ![完全なソリューション分析 チェック ボックスを有効にします。] (../code-quality/media/fsa_toolsoptions.png "FSA_ToolsOptions")

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>結果を有効にして、完全なソリューション分析を無効にします。

次のスクリーン ショットでは、完全なソリューション分析を有効にすると、結果を確認できます。 すべてのエラーとコード分析の問題で*すべて*ソリューション内のファイルの表示、かどうか、ファイルが開いているかに関係なく。

![完全ソリューション解析を有効にします。] (../code-quality/media/fsa_enabled.png "FSA_Enabled")

次のスクリーン ショットは、完全なソリューション分析を無効にした後、同じソリューションからの結果を示します。 エラーとでコード分析の問題だけは、エラー一覧にファイルが表示されるソリューションを開きます。

![完全ソリューション解析を無効になっています。] (../code-quality/media/fsa_disabled.png "FSA_Disabled")

## <a name="automatically-disabling-full-solution-analysis"></a>完全なソリューション分析を自動的に無効化

Visual Studio では、ことが検出された場合 200 MB に使用できるシステム メモリの少ないが、自動的に無効に完全なソリューション分析 (およびその他の機能) が有効な場合またはします。 この場合、これを通知するアラートが表示されます。 ボタンには、必要な場合に、完全なソリューション分析を再度有効にすることができます。

![完全ソリューション解析を中断する警告テキスト](../code-quality/media/fsa_alert.png "FSA_Alert")