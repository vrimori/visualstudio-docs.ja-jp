---
title: "方法: コード分析チェックイン ポリシーの保守が容易なコードを適用する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 80f3d2385fa1023637081b787c8d938ae42f79b4
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2018
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>方法: コード分析チェックイン ポリシーの保守が容易なコードを適用します。

開発者は、複雑さ、そのコードの保守容易性を測定する、コード メトリックスのツールを使用できますが、チェックイン ポリシーの一部としてコード メトリックスを呼び出すことはできません。 ただし、コード メトリックスの基準に、コードの準拠を確認するコード分析規則を有効にし、チェックイン ポリシーによって規則を実施できます。 コード メトリックスの詳細については、次を参照してください。[コード メトリックス値](../code-quality/code-metrics-values.md)です。

継承の深さ、クラス結合度、保守容易性指数、および複雑性ルールをコード分析チェックイン ポリシーを使用して保守が容易なコードを適用するを有効にすることができます。 これらのルールの 4 つすべてをコード分析ポリシー エディターで「保守容易性規則」カテゴリの下ではあります。

Team foundation バージョン管理の管理者は、チェックイン ポリシー要件にコード分析の保守容易性規則を追加できます。 これらのチェックイン ポリシーでチェックインを開始する前に、これらの規則の変更に基づいて、コード分析を実行する開発者は必要です。

## <a name="to-open-the-code-analysis-policy-editor"></a>コード分析ポリシー エディターを開く

1. で**チーム エクスプ ローラー**、チーム プロジェクトを右クリックし、をクリックして**チーム プロジェクトの設定**、クリックして**ソース管理**です。

     The **Source Control** dialog box appears.

2. で、**チェックイン ポリシーによって**タブをクリックし、をクリックして**追加**です。

     The **Add Check-in Policy** dialog box appears.

3. で、**チェックイン ポリシーによって**一覧で、、**コード分析**チェック ボックスをクリックして**OK**です。

     The **Code Analysis Policy Editor** dialog box appears.

## <a name="to-enable-code-analysis-maintainability-rules"></a>コード分析の保守容易性の規則を有効にするには

1. で、**コード分析ポリシー エディター**ダイアログ ボックスで、**ルール設定**、展開、**保守容易性規則**ノード。

2. では、次のルールのチェック ボックスを選択します。

    -   継承の深さ: **CA1501 AvoidExcessiveInheritance** -しきい値: 複数の 5 レベルの深さで警告

    -   複雑さ: **CA1502 AvoidExcessiveComplexity** -しきい値: 25 以上の警告

    -   保守容易性指数: **CA1505 AvoidUnmaintainableCode** -しきい値: 20 未満の警告

    -   クラスの結合: **CA1506 AvoidExcessiveClassCoupling** -しきい値: クラスの 80 以上とメソッドの 30 以上の警告

    さらに、ビルドの成功を防ぐために規則違反する場合は、選択、**警告をエラーとして扱う**規則の説明の横にあるチェック ボックスです。

3.  **OK**です。 新しいチェックイン ポリシーは、将来のチェックインを今すぐに適用されます。

## <a name="see-also"></a>関連項目

[コード メトリックス値](../code-quality/code-metrics-values.md)
[の作成とコード分析チェックイン ポリシーを使用します。](../code-quality/creating-and-using-code-analysis-check-in-policies.md)