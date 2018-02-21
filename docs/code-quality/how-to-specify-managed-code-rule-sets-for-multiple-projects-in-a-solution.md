---
title: "方法: ソリューション内の複数のプロジェクトに対してマネージ コード規則セットを指定して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.solution
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: e0b6a2864340f87702b765f49605ebdb3aaa555c
ms.sourcegitcommit: bfa26fd7426af0d065cb2eef3d6827b5d6f7986c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2018
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>方法: ソリューション内の複数のプロジェクトに対してマネージ コード規則セットを指定する

既定では、ソリューションのすべてのマネージ プロジェクトには Microsoft 最小推奨規則コード分析を割り当てられた*ルール セット*です。 ソリューションのプロパティ ダイアログ ボックスで、ソリューションのプロジェクトに割り当てられる規則セットを変更できます。

> [!NOTE]
> 既定では、プロジェクトのコード分析はビルド ステップとして実行されません。 ビルド ステップとしてコード分析を有効にするを参照してください。[する方法: マネージ コード プロジェクトのコード分析を構成する](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)です。

1. Visual Studio でソリューションを開きます。

2. **分析** メニューのをクリックして**ソリューションのコード分析を構成する**です。

3. 必要に応じて、展開**共通プロパティ**、クリックして**コード分析設定**です。

4. 1 つ以上のプロジェクトに対して規則セットを指定できます。

    - 個々のプロジェクトに対して規則セットを指定するには、プロジェクト名をクリックします。

    - 複数のプロジェクトに対して規則セットを指定するには、Ctrl キーを押しながらプロジェクト名をクリックします。

    - ソリューションに含まれるすべてのプロジェクトを指定するには、Shift キーを押しながらプロジェクトの一覧内をクリックします。

5. クリックして、**ルール セット**フィールドのプロジェクトとセットを適用するルールの名前をクリックします。