---
title: '方法: アクティビティ ライブラリを作成 |Microsoft ドキュメント'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: faa7c593d27474c0980e7c7df7bf932bd2d5431d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-an-activity-library"></a>アクティビティ ライブラリを作成する方法
カスタム アクティビティは、ワークフローで特定のビジネス プロセスをモデル化するために使用されます。 アクティビティ ライブラリ テンプレートで[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]視覚的に、Windows ワークフロー デザイナーを使用してこのようなカスタム アクティビティを作成するために用意されています。

### <a name="to-create-a-workflow-activity-library"></a>ワークフロー アクティビティ ライブラリを作成するには

1.  [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] を起動します。

2.  **ファイル**] メニューのをポイント**新規**、し、[**プロジェクト.**.

     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

3.  **プロジェクトの種類**ペインで、**ワークフロー**いずれかから、 **Visual c#**プロジェクトまたは**Visual Basic**に応じてグループ化、言語の優先順位。

4.  **テンプレート**ペインで、**アクティビティ ライブラリ**です。

5.  **名前** ボックスを識別しやすく、プロジェクトのわかりやすい名前を入力します。

6.  **場所**ボックスで、プロジェクトを保存ディレクトリ タイプで**参照**まで移動します。

7.  **ソリューション**ボックスに、ソリューションのわかりやすい名前を入力し、をクリックして**OK**です。

    > [!NOTE]
    > ワークフロー コンソール アプリケーションを既存のソリューションに追加する場合でそのソリューションを開きます[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]で、ソリューションを右クリックして**ソリューション エクスプ ローラー**を選択して**追加**、し**新しいプロジェクト.**を開くには、**新しいプロジェクト** ダイアログ ボックス。 上記の手順を実行します。

8.  プロジェクト テンプレートによって、XAML でアクティビティ定義が作成されます。 Windows ワークフロー デザイナーが開き、カスタム アクティビティ用のキャンバスを表示します。

9. アクティビティをドラッグして、**ツールボックス**に、カスタム アクティビティに含めるデザイン画面にします。

    > [!CAUTION]
    > カスタム アクティビティの本体に含めることができる子アクティビティは 1 つのみです。ただし、その子アクティビティは、<xref:System.Activities.Statements.Sequence> アクティビティや <xref:System.Activities.Statements.Flowchart> アクティビティなどの複合アクティビティにすることができます。

## <a name="see-also"></a>関連項目

- [アクティビティを作成する方法](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)
- [ワークフロー プロジェクトの作成](../workflow-designer/creating-a-workflow-project.md)