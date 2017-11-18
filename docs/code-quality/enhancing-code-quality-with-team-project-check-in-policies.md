---
title: "チーム プロジェクト チェックイン ポリシーによるコード品質の向上 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
ms.assetid: 0ab72c33-148a-4a8a-a7bf-046995514c84
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5b421f5512e51d83e7f6e4edfbbe2869a1484200
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>チーム プロジェクト チェックイン ポリシーによるコード品質の向上
Team Foundation バージョン コントロール (TFVC) を使用する場合は、チーム プロジェクトのチェックイン ポリシーを作成して、 コードの品質向上とグループ開発の効率化を実現するための対策を適用できます。 チェックイン ポリシーとは、チーム プロジェクト レベルで設定され、コードをチェックインする前に開発者のコンピューターに適用される規則です。  
  
 これらのチーム プロジェクト チェックイン ポリシーを指定できます。  
  
-   **ビルド**： ビルド中に作成されたビルド ブレークが新しいチェックインの前に修正されていることを必須とします。  
  
-   **変更セットのコメント**: 変更をチェックインするときにユーザーがコメントを指定することを必須とします。  
  
-   **コード分析**: チェックインの前にコード分析を実行することを必須とします。  
  
-   **作業項目**: 1 つ以上の作業項目をチェックインに関連付けることを必須とします。  
  
> [!IMPORTANT]
>  チェックイン ポリシーを使用するには、 [!INCLUDE[vststfsLong](../code-quality/includes/vststfslong_md.md)]に接続する必要があります。  
  
## <a name="common-tasks"></a>一般的なタスク  
  
|タスク|関連する参照先|  
|----------|------------------------|  
|**チェックイン ポリシーの作成と使用:** [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)]のチーム プロジェクトの設定を使用して、チェックイン ポリシーを作成します。|[品質ゲートの設定と適用](http://msdn.microsoft.com/Library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**コード分析チェックイン ポリシーの作成と使用:** コード分析規則の標準セットから選択することも、独自の規則セットを作成することもできます。|[コード分析を用いたチェックイン ポリシーの作成と使用](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|  
  
## <a name="related-tasks"></a>関連タスク  
  
|タスク|関連する参照先|  
|----------|------------------------|  
|**開発環境の設定:** コードを作成または変更する前に、適切なソース コードを使用して開発環境およびテスト環境を設定する必要があります。 データベースを使用している場合は、そのデータベースのオフライン形式へのアクセス権も必要です。|[開発環境の設定](http://msdn.microsoft.com/en-us/7b686610-d379-4ca0-9608-73ef0e576e3a)|  
|**開発プロセスにおけるコード分析の使用:** チームのメンバーは、それぞれの開発コンピューターでコード分析を実行します。 Visual Studio では、開発者が個々のコード プロジェクトについてコード分析を構成および実行し、実行したコード分析で発見された問題を表示および分析して、警告用の作業項目を作成します。|[アプリケーション品質の分析](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|  
|**単体テストの作成および実行:** 単体テストを実行することにより、開発者およびテスト担当者は、C#、Visual Basic、.NET、および C++ のプロジェクトでクラスのメソッドに論理エラーがないかどうかをすばやく確認できます。 単体テストは、1 回作成するだけでよく、バグが追加されていないことを確認するために、ソース コードが変更されるたびに実行できます。|[コードの単体テスト](../test/unit-test-your-code.md)|  
|**作業項目と欠陥の追跡:** 作業項目を使用して、自分の作業とチーム プロジェクトに関する情報の両方を、追跡および管理できます。 作業項目は [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] が作業の割り当てと進行状況を追跡するために使用するデータベース レコードです。 さまざまな種類の作業項目を使用して、顧客要件、製品バグ、開発タスクなどの作業を追跡できます。|[作業の追跡し管理ワークフロー &#91; リダイレクト &#93;です。](http://msdn.microsoft.com/en-us/d2d8637d-0ef8-4ca3-874e-a04713344032)|  
  
## <a name="external-resources"></a>外部リソース  
  
### <a name="guidance"></a>ガイダンス  
 [Visual Studio 2012 を使用した継続的配信のためのテスト - 第 2 章: 単体テスト: 内部のテスト](http://go.microsoft.com/fwlink/?LinkID=255188)