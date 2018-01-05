---
title: "方法: コード分析チェックイン ポリシーの保守が容易なコードを適用する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 19d8761abea6934c59673c332ea09e8a0b4e6997
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>方法: コード分析のチェックイン ポリシーを使用して保守が容易なコードを適用する
開発者は、複雑さ、そのコードの保守容易性を測定する、コード メトリックスのツールを使用できますが、チェックイン ポリシーの一部としてコード メトリックスを呼び出すことはできません。 ただし、チームは、そのコードのコード メトリックスの標準に準拠を確認し、チェックイン ポリシーを使用して、ルールを適用するコード分析規則を有効にできます。 コード メトリックスの詳細については、次を参照してください。、[コード メトリックス値](../code-quality/code-metrics-values.md)です。  
  
 開発者は、継承の深さ、クラス結合度、保守容易性指数、および複雑性ルール コード分析チェックイン ポリシーを使用して保守が容易なコードを適用するに有効にすることができます。 これらのルールの 4 つすべてをコード分析ポリシー エディターで「保守容易性規則」カテゴリの下ではあります。  
  
 バージョンの管理者が制御[!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]チェックイン ポリシーの要件にコード分析の保守容易性規則を追加することができます。 これらのチェックイン ポリシーでチェックインを開始する前に、これらの規則の変更に基づいて、コード分析を実行する開発者は必要です。  
  
### <a name="to-open-the-code-analysis-policy-editor"></a>コード分析ポリシー エディターを開く  
  
1.  **チーム エクスプ ローラー**、チーム プロジェクトを右クリックし、をクリックして**チーム プロジェクトの設定**、クリックして**ソース管理**です。  
  
     **ソース管理** ダイアログ ボックスが表示されます。  
  
2.  **チェックイン ポリシーによって**タブをクリックし、をクリックして**追加**です。  
  
     **チェックイン ポリシーを追加する** ダイアログ ボックスが表示されます。  
  
3.  **チェックイン ポリシーによって**一覧で、、**コード分析**チェック ボックスをクリックして**OK**です。  
  
     **コード分析ポリシー エディター**  ダイアログ ボックスが表示されます。  
  
### <a name="to-enable-code-analysis-maintainability-rules"></a>コード分析の保守容易性の規則を有効にするには  
  
1.  **コード分析ポリシー エディター**ダイアログ ボックスで、**ルール設定**、展開、**保守容易性規則**ノード。  
  
2.  次のルールのチェック ボックスを選択します。  
  
    -   継承の深さ: **CA1501 AvoidExcessiveInheritance** -しきい値: 複数の 5 レベルの深さで警告  
  
    -   複雑さ: **CA1502 AvoidExcessiveComplexity** -しきい値: 25 以上の警告  
  
    -   保守容易性指数: **CA1505 AvoidUnmaintainableCode** -しきい値: 20 未満の警告  
  
    -   クラスの結合: **CA1506 AvoidExcessiveClassCoupling** -しきい値: クラスの 80 以上とメソッドの 30 以上の警告  
  
    -   さらに、規則違反を防ぐため、ビルドする場合は、選択、**警告をエラーとして扱う**規則の説明の横にあるチェック ボックスです。  
  
3.  **[OK]**をクリックします。 新しいチェックイン ポリシーは、将来のチェックインを今すぐに適用されます。  
  
## <a name="see-also"></a>参照  
 [コード メトリックス値](../code-quality/code-metrics-values.md)   
 [コード分析を用いたチェックイン ポリシーの作成と使用](../code-quality/creating-and-using-code-analysis-check-in-policies.md)