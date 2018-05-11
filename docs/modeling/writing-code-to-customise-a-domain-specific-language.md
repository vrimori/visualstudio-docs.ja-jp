---
title: ドメイン固有言語をカスタマイズします。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: f7fd63546f7d85ddbcc7661ac600a56bd340e6ec
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="write-code-to-customize-a-domain-specific-language"></a>ドメイン固有言語をカスタマイズするためのコードを記述します。

このセクションでは、カスタム コードを使用して、アクセス、変更、またはドメイン固有言語でモデルを作成する方法を示しています。

DSL で動作するコードを記述できるいくつかのコンテキストがあります。

-   **カスタム コマンド。** ダイアグラムを右クリックしてユーザーが呼び出すことができます、モデルを変更するコマンドを作成することができます。 詳細については、次を参照してください。[する方法: ショートカット メニューにコマンドを追加](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)です。

-   **検証。** モデルが正しい状態であることを検証するコードを記述することができます。 詳細については、次を参照してください。[ドメイン固有言語で検証](../modeling/validation-in-a-domain-specific-language.md)です。

-   **既定の動作をオーバーライドします。** DslDefinition.dsl から生成されるコードの多くの側面を変更することができます。 詳細については、次を参照してください。[をオーバーライドすると、生成されたクラスを拡張する](../modeling/overriding-and-extending-the-generated-classes.md)です。

-   **テキスト変換します。** モデルにアクセスし、プログラム コードを生成する例については、テキスト ファイルを生成するコードを含むテキスト テンプレートを記述することができます。 詳細については、次を参照してください。[ドメイン固有言語から、コードの生成](../modeling/generating-code-from-a-domain-specific-language.md)です。

-   **他の Visual Studio 拡張機能です。** 読み取りし、モデルの変更を別の VSIX 拡張機能を記述することができます。 詳細については、次を参照してください[する方法: プログラム コード内のファイルからモデルを開く。](../modeling/how-to-open-a-model-from-file-in-program-code.md)

DslDefinition.dsl で定義するクラスのインスタンスと呼ばれるデータ構造が保持されており、*メモリ内ストア*(IMS) または*ストア*です。 DSL で常に定義したクラスは、コンス トラクターに引数としてストアを取得します。 たとえば、DSL の例と呼ばれるクラスを定義するとします。

`Example element = new Example (theStore);`

(単に通常のオブジェクト) ではなく、ストア内のオブジェクトを保存すると、いくつかの利点が提供します。

-   **トランザクション**です。 一連のトランザクションに関連する変更をグループ化することができます。

     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

     `{`

     `// make several changes to Store elements here`

     `t.Commit();`

     `}`

     最終的な Commit() が実行されないように、変更中に例外が発生する場合、ストアが前の状態にリセットされます。 これにより、エラーが残されていないモデルを矛盾した状態になっていることを確認できます。 詳細については、次を参照してください。[を移動すると、プログラム コードでモデルを更新する](../modeling/navigating-and-updating-a-model-in-program-code.md)です。

-   **二項関係**です。 2 つのクラス間のリレーションシップを定義する場合、両方の端をインスタンスはもう一方の端に移動するプロパティを持ちます。 2 つの端は、常に同期します。 たとえば、親と子をという名前のロールの親のリレーションシップを定義した場合は、次のでしたに記述します。

     `John.Children.Add(Mary)`

     次の式の両方に該当するようになりました。

     `John.Children.Contains(Mary)`

     `Mary.Parents.Contains(John)`

     記述して、同じ効果を得ることができますも。

     `Mary.Parents.Add(John)`

     詳細については、次を参照してください。[を移動すると、プログラム コードでモデルを更新する](../modeling/navigating-and-updating-a-model-in-program-code.md)です。

-   **ルールとイベント**です。 指定された変更が加えられるたびに発生するルールを定義できます。 ルールは、たとえば、ダイアグラムでの図形提示することがモデル要素を持つ最新の状態に保つを使用します。 詳細については、次を参照してください。[への応答と変更を反映する](../modeling/responding-to-and-propagating-changes.md)です。

-   **シリアル化**です。 ストアは、標準的なファイルが含まれているオブジェクトをシリアル化する方法を提供します。 シリアル化と逆シリアル化のルールをカスタマイズすることができます。 詳細については、次を参照してください。[ファイル記憶域のカスタマイズと XML シリアル化](../modeling/customizing-file-storage-and-xml-serialization.md)です。

## <a name="see-also"></a>関連項目

- [ドメイン固有言語のカスタマイズおよび拡張](../modeling/customizing-and-extending-a-domain-specific-language.md)