---
title: Visual Studio でカスタム コード分析ルールを作成します。
ms.date: 04/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3b1d9b436c3e3be4f241d18791744085be4ece9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920691"
---
# <a name="custom-rule-sets"></a>カスタム規則セット

特定のプロジェクトにあわせて必要なコード分析の *カスタム ルール セット* を作成することができます。

## <a name="create-a-custom-rule-set"></a>カスタム規則セットを作成します。

カスタム規則セットを作成、組み込みの規則セットを開くことができます、**ルール セット エディター**です。 ルールに違反したときに発生するアクションを変更することができ、そこから、追加するか、特定の規則を削除する&mdash;など、警告またはエラーを表示します。

1. **ソリューション エクスプ ローラー**、プロジェクトを右クリックし、**プロパティ**です。

2. **プロパティ**ページ、select、**コード分析**タブです。

3. **この規則セットを実行**ドロップダウン リストで、次のいずれかの操作を行います。

    - カスタマイズする規則セットを選択します。

     \- または -

    - 選択 **\<[参照...] >** 既存の規則セットを指定ではありません、ボックスの一覧です。

4. 選択**開く**規則セット エディターで規則を表示します。

新しいルール セット ファイルを作成することも、**新しいファイル** ダイアログ。

1. 選択**ファイル** > **新規** > **ファイル**、またはキーを押して**Ctrl**+**N**.

2. **新しいファイル**ダイアログ ボックスで、**全般**、左側のカテゴリを選択し、**コード分析規則セット**です。

3. **[開く]** を選択します。

   新しい *.ruleset*規則セット エディターでファイルが開きます。

### <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>複数の規則セットから設定するカスタム ルールを作成します。

1. ソリューション エクスプ ローラーでプロジェクトを右クリックし、**プロパティ**です。

2. **プロパティ**ページ、select、**コード分析**タブです。

3. 選択**\<複数ルールの設定... を選択 >** から**この規則セットを実行**です。

4. **の追加と削除規則セット**を新しいルール セットに含めるダイアログ ボックスで、ルール セットを選択します。

   ![追加または削除する規則セット ダイアログ ボックス](media/add-remove-rule-sets.png)

5. 選択**名前を付けて保存**の名前を入力、 *.ruleset*ファイルをクリックし **保存**です。

   新しい規則セットが選択されて、**この規則セットを実行** ボックスの一覧です。

6. 選択**開く**を開くには、新しい規則が規則セット エディターで設定します。

## <a name="name-and-description"></a>名前と説明

エディターで開かれている規則セットの表示名を変更するには、開く、**プロパティ**ウィンドウを選択して**ビュー** > **プロパティ ウィンドウ**メニュー バーでします。 表示名を入力、**名前**ボックス。 ルール セットの説明を入力することもできます。

## <a name="next-steps"></a>次の手順

これで、ルール セットがある場合は、次の手順は、追加やルールの削除規則違反の重要度を変更して、ルールをカスタマイズするは。

> [!div class="nextstepaction"]
> [規則セット エディターで規則を変更します。](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>関連項目

- [方法: マネージ コード プロジェクトのコード分析を構成する](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [コード分析規則セットの参照](../code-quality/rule-set-reference.md)
