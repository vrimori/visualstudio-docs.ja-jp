---
title: "Visual Studio でのコード生成機能 | Microsoft Docs"
ms.custom: 
ms.date: 01/11/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 7740fcea4ac944242f4284382cf26544d9ea95b5
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="code-generation-features-in-visual-studio"></a>Visual Studio でのコード生成機能

Visual Studio には、エディターでコードを生成する多くの方法があります。 これらのコード生成機能を使用すると、時間を短縮し、キーボード操作や構文エラーを減らし、コード全体の一貫性を向上できます。

Visual Studio のコード生成機能の一部には、[コード スニペット](../ide/code-snippets.md)と[クイック アクション](../ide/quick-actions.md) ![小さい電球アイコン](media/vs2015_lightbulbsmall.png) があります。

[クイック アクション](../ide/quick-actions.md)で使用できる共通のコード生成タスクは、次のとおりです。

* クラス、メソッド、プロパティなどの生成

* 抽象クラスまたはインターフェイスの実装

* 複合式へのローカル変数の導入

さらに、特定の文字を入力することで以下を実行できます。

* コード用の [XML 形式のコメント ブロック]()の生成。ドキュメントを自動生成するために、後で処理できます。

* [メソッド上書き]()シグネチャの生成

コード生成のロジックは言語の構文に密接に結び付けられているため、Visual Studio の各言語サービスには、それぞれ独自のコード生成機能があります。

## <a name="see-also"></a>関連項目

[クイック アクション](../ide/quick-actions.md)  
[コード スニペット](../ide/code-snippets.md)  
[コード生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)  
[リファクタリング](../ide/refactoring-in-visual-studio.md)