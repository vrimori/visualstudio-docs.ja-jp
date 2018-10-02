---
title: '方法: コード分析チェックイン ポリシーを保守しやすいコードを適用する |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 97b321fe5a72c6f3ace680476340eca48f7ed309
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545978"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>方法: コード分析のチェックイン ポリシーを使用して保守が容易なコードを適用する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: コード分析チェックイン ポリシーを保守しやすいコードを強制](https://docs.microsoft.com/visualstudio/code-quality/how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy)します。  
  
開発者は、複雑さとして、コードの保守容易性を測定する、コード メトリックスのツールを使用できますが、コード メトリックスをチェックイン ポリシーの一部として呼び出されることはできません。 ただし、チームは、コードのコード メトリックスの標準に準拠の確認し、チェックイン ポリシーを使用したルールを適用するコード分析規則を有効にできます。 コード メトリックスの詳細については、次を参照してください。、[コード メトリックス値](../code-quality/code-metrics-values.md)します。  
  
 開発者は、Depth of Inheritance、Class Coupling、保守容易性指数、および複雑さのルール コード分析チェックイン ポリシーを保守しやすいコードを適用するに有効にすることができます。 これらのルールの 4 つすべては、「保守容易性規則」カテゴリで、コード分析ポリシー エディターで表示されます。  
  
 バージョンの管理者が制御[!INCLUDE[esprfound](../includes/esprfound-md.md)]チェックイン ポリシーの要件にコード分析の保守容易性の規則を追加することができます。 これらのチェックイン ポリシーがコード分析のチェックインを開始する前に、これらの規則の変更に基づいて実行する開発者が必要です。  
  
### <a name="to-open-the-code-analysis-policy-editor"></a>コード分析ポリシー エディターを開きます  
  
1.  **チーム エクスプ ローラー**、チーム プロジェクトを右クリックし、をクリックして**チーム プロジェクトの設定**、 をクリックし、**ソース管理**します。  
  
     **ソース管理** ダイアログ ボックスが表示されます。  
  
2.  **チェックイン ポリシー**タブをクリックし、をクリックして**追加**します。  
  
     **チェックイン ポリシーの追加** ダイアログ ボックスが表示されます。  
  
3.  **チェックイン ポリシー**一覧で、、**コード分析**チェック ボックスをオンにし**OK**。  
  
     **コード分析ポリシー エディター**  ダイアログ ボックスが表示されます。  
  
### <a name="to-enable-code-analysis-maintainability-rules"></a>コード分析の保守容易性の規則を有効にするには  
  
1.  **コード分析ポリシー エディター**ダイアログ ボックスで、**ルール設定**、展開、**保守容易性規則**ノード。  
  
2.  次の規則のチェック ボックスを選択します。  
  
    -   継承の深さ: **CA1501 AvoidExcessiveInheritance** -しきい値: 深さは 5 以上のレベルで警告が発生  
  
    -   複雑さ: **CA1502 AvoidExcessiveComplexity** -しきい値: 25 以上の警告  
  
    -   保守容易性指数: **CA1505 AvoidUnmaintainableCode** -しきい値: 20 未満で警告が発生  
  
    -   クラス結合度: **CA1506 AvoidExcessiveClassCoupling** -しきい値: クラスの 80 以上とメソッドの 30 以上で警告が発生  
  
    -   さらに、ビルドをできないようにするルールに違反する場合は、選択、**警告をエラーとして扱う**ルールの説明の横にあるチェック ボックス。  
  
3.  **[OK]** をクリックします。 新しいチェックイン ポリシーは、将来のチェックインに適用されます。  
  
## <a name="see-also"></a>関連項目  
 [コード メトリックス値](../code-quality/code-metrics-values.md)   
 [コード分析を用いたチェックイン ポリシーの作成と使用](../code-quality/creating-and-using-code-analysis-check-in-policies.md)



