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
ms.openlocfilehash: 727c11e24eb3409de89fe211c6a37691dfec298c
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204116"
---
# <a name="customize-a-rule-set"></a>ルール セットをカスタマイズします。

コード分析のための特定のプロジェクトのニーズに合わせて設定、カスタム規則を作成することができます。

## <a name="create-a-custom-rule-set"></a>カスタム規則セットを作成します。

カスタム ルールを作成するには設定、組み込みの規則セットを開くことができます、**ルール セット エディター**します。 ルールに違反したときに発生するアクションを変更して、そこから追加または特定の規則を削除&mdash;など、警告またはエラーを表示します。

1. **ソリューション エクスプ ローラー**、プロジェクトを右クリックし、**プロパティ**します。

2. **プロパティ**ページで、**コード分析**タブ。

3. **この規則セットを実行**ドロップダウン リストで、次のいずれかの操作を行います。

    - カスタマイズする規則セットを選択します。

     \- または -

    - 選択 **\<[参照...] >** を既存の規則セットを指定されていないリスト。

4. 選択**オープン**ルール セット エディターで、ルールを表示します。

新しい規則セット ファイルを作成することも、**新しいファイル**ダイアログ。

1. 選択**ファイル** > **新規** > **ファイル**、またはキーを押します**Ctrl**+**N**.

2. **新しいファイル**ダイアログ ボックスで、**全般**、左側のカテゴリを選び**コード分析規則セット**します。

3. **[開く]** を選択します。

   新しい *.ruleset*規則セット エディターでファイルが開きます。

### <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>カスタムの規則セットを複数の規則セットからの作成します。

1. ソリューション エクスプ ローラーでプロジェクトを右クリックしを選択し、**プロパティ**します。

2. **プロパティ**ページで、**コード分析**タブ。

3. 選択**\<複数ルールの設定... を選択 >** から**この規則セットを実行**します。

4. **の追加と削除規則セット**を新しいルール セットに含める ダイアログ ボックスで、ルール セットを選択します。

   ![追加または削除ルール セット ダイアログ ボックス](media/add-remove-rule-sets.png)

5. 選択**名前を付けて保存**の名前を入力、 *.ruleset*ファイルを選び**保存**します。

   新しい規則セットが選択されて、**この規則セットを実行**一覧。

6. 選択**開く**をルール セット エディターで設定する新しい規則を開きます。

## <a name="name-and-description"></a>名前と説明

エディターで開かれている規則セットの表示名を変更するには、開く、**プロパティ**ウィンドウを選択して**ビュー** > **プロパティ ウィンドウ**メニュー バーでします。 表示名を入力、**名前**ボックス。 ルール セットの説明を入力することもできます。

## <a name="next-steps"></a>次の手順

これでルール セットがある場合は、次の手順が追加や、ルールを削除規則違反の重大度を変更することによって、規則をカスタマイズします。

> [!div class="nextstepaction"]
> [規則セット エディターで規則を変更します。](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>関連項目

- 
  [方法: マネージド コード プロジェクトのコード分析を構成する](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [コード分析規則セットの参照](../code-quality/rule-set-reference.md)