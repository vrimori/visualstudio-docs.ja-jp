---
title: '方法: コード分析のチェックイン ポリシーを使用して保守が容易なコードを適用する'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7d31e52ab2f158b73a0076414b6d18e0b7421b04
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825718"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>方法: コード分析チェックイン ポリシーを保守しやすいコードを適用します。

開発者は、複雑さとして、コードの保守性を測定する、コード メトリックスのツールを使用できますが、チェックイン ポリシーの一部としてコード メトリックスを呼び出すことはできません。 ただし、コードのメトリックの標準の準拠をコードのことを確認するコード分析規則を有効にし、チェックイン ポリシーを使用した、ルールを適用できます。 コード メトリックスの詳細については、次を参照してください。[コード メトリックス値](../code-quality/code-metrics-values.md)します。

Depth of Inheritance、Class Coupling、保守容易性指数、および複雑さのルール コード分析チェックイン ポリシーを保守しやすいコードを適用するのには、有効にできます。 これらのルールの 4 つすべては、「保守容易性規則」カテゴリで、コード分析ポリシー エディターで表示されます。

Team foundation バージョン管理の管理者は、チェックイン ポリシーの要件をコード分析の保守容易性の規則を追加できます。 これらのチェックイン ポリシーがコード分析のチェックインを開始する前に、これらの規則の変更に基づいて実行する開発者が必要です。

## <a name="to-open-the-code-analysis-policy-editor"></a>コード分析ポリシー エディターを開く

1. **チーム エクスプ ローラー**、プロジェクトを右クリックし、をクリックして**プロジェクト設定**、 をクリックし、**ソース管理**します。

     **ソース管理** ダイアログ ボックスが表示されます。

2. **チェックイン ポリシー**タブをクリックし、をクリックして**追加**します。

     **チェックイン ポリシーの追加** ダイアログ ボックスが表示されます。

3. **チェックイン ポリシー**一覧で、、**コード分析**チェック ボックスをオンにし**OK**。

     **コード分析ポリシー エディター**  ダイアログ ボックスが表示されます。

## <a name="to-enable-code-analysis-maintainability-rules"></a>コード分析の保守容易性の規則を有効にするには

1. **コード分析ポリシー エディター**ダイアログ ボックスで、**ルール設定**、展開、**保守容易性規則**ノード。

2. 次の規則のチェック ボックスを選択します。

   - 継承の深さ:**CA1501 AvoidExcessiveInheritance** -しきい値。5 つを超えるレベルの深さで警告が発生

   - 複雑さ:**CA1502 AvoidExcessiveComplexity** -しきい値。25 を超えるで警告が発生

   - 保守容易性指数。**CA1505 AvoidUnmaintainableCode** -しきい値。20 未満で警告が発生

   - クラス結合度:**CA1506 AvoidExcessiveClassCoupling** -しきい値。クラスの 80 以上とメソッドの 30 以上で警告が発生

     さらに、成功したビルドを防ぐために規則違反する場合は、選択、**警告をエラーとして扱う**ルールの説明の横にあるチェック ボックス。

3. **[OK]** をクリックします。 新しいチェックイン ポリシーは、将来のチェックインに適用されます。

## <a name="see-also"></a>関連項目

- [コード メトリックス値](../code-quality/code-metrics-values.md)
- [作成とコード分析チェックイン ポリシーの使用](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)