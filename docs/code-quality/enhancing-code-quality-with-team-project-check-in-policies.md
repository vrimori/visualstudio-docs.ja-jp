---
title: "チーム プロジェクト チェックイン ポリシーによるコード品質の向上 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c82bc929fa7633719c06569cb3dded5df651a349
ms.sourcegitcommit: e5bd950df79175a96fe62b3d4b17a3ef536ec4c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>チーム プロジェクト チェックイン ポリシーによるコード品質の向上

Team Foundation バージョン コントロール (TFVC) を使用する場合は、チーム プロジェクトのチェックイン ポリシーを作成して、 コードの品質向上とグループ開発の効率化を実現するための対策を適用できます。 チェックイン ポリシーとは、チーム プロジェクト レベルで設定され、コードをチェックインする前に開発者のコンピューターに適用される規則です。

これらのチーム プロジェクト チェックイン ポリシーを指定できます。

- **ビルド**： ビルド中に作成されたビルド ブレークが新しいチェックインの前に修正されていることを必須とします。

- **変更セットのコメント**: 変更をチェックインするときにユーザーがコメントを指定することを必須とします。

- **コード分析**: チェックインの前にコード分析を実行することを必須とします。

- **作業項目**: 1 つ以上の作業項目をチェックインに関連付けることを必須とします。

> [!IMPORTANT]
> チェックイン ポリシーを使用するには、 [!INCLUDE[vststfsLong](../code-quality/includes/vststfslong_md.md)]に接続する必要があります。

## <a name="common-tasks"></a>一般的なタスク

|タスク|関連する参照先|
|----------|------------------------|
|**コード分析チェックイン ポリシーの作成と使用:** コード分析規則の標準セットから選択することも、独自の規則セットを作成することもできます。|[コード分析を用いたチェックイン ポリシーの作成と使用](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|

## <a name="related-tasks"></a>関連タスク

|タスク|関連する参照先|
|----------|------------------------|
|**開発プロセスにおけるコード分析の使用:** チームのメンバーは、それぞれの開発コンピューターでコード分析を実行します。 Visual Studio では、開発者が個々のコード プロジェクトについてコード分析を構成および実行し、実行したコード分析で発見された問題を表示および分析して、警告用の作業項目を作成します。|[アプリケーション品質の分析](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|
|**作成し、単体テストを実行します。**単体テストが、c#、Visual Basic、および C++ のプロジェクトでクラスのメソッドのロジック エラーを確認する簡単な方法の開発者とテスト担当者を提供します。 単体テストは、1 回作成するだけでよく、バグが追加されていないことを確認するために、ソース コードが変更されるたびに実行できます。|[コードの単体テスト](../test/unit-test-your-code.md)|
|**作業項目と欠陥の追跡:** 作業項目を使用して、自分の作業とチーム プロジェクトに関する情報の両方を、追跡および管理できます。 作業項目は [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] が作業の割り当てと進行状況を追跡するために使用するデータベース レコードです。 さまざまな種類の作業項目を使用して、顧客要件、製品バグ、開発タスクなどの作業を追跡できます。|[作業項目 (VSTS)](/vsts/work/work-items/index)|

## <a name="external-resources"></a>外部リソース

[Visual Studio 2012 を使用した継続的配信のためのテスト - 第 2 章: 単体テスト: 内部のテスト](http://go.microsoft.com/fwlink/?LinkID=255188)