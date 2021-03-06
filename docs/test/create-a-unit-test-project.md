---
title: 単体テスト プロジェクトを作成する
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: e90aa1f8fe13bc7ee99f3ac20b1813ca2a6c9672
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996815"
---
# <a name="create-a-unit-test-project"></a>単体テスト プロジェクトを作成する

単体テストでは、多くの場合、テスト対象のコードの構造を再現します。 たとえば、製品のコード プロジェクトごとに単体テスト プロジェクトを作成します。 テスト プロジェクトは本稼働コードと同じソリューションに置くことも、別個のソリューションに置くこともできます。 1 つのソリューションに複数の単体テスト プロジェクトを置くこともできます。

> [!NOTE]
> ネイティブ コードの単体テストの場所とテスト プロジェクトの構造は、このトピックの説明にある構造とは異なっていても構いません。 詳細については、「[C/C++ 用の単体テストの記述](writing-unit-tests-for-c-cpp.md)」を参照してください。

## <a name="to-create-a-unit-test-project"></a>単体テスト プロジェクトを作成するには:

1.  **[ファイル]** メニューの **[新規作成]** をクリックし、**[プロジェクト]** をクリックします (キーボード: **Ctrl** + **Shift** + **N**)。

2.  **[新しいプロジェクト]** ダイアログ ボックスで、**[インストール済み]** ノードを展開して、テスト プロジェクトで使用する言語を選択し、**[テスト]** をクリックします。

3.  Microsoft 単体テスト フレームワークの 1 つを使用するには、プロジェクト テンプレートの一覧から **[単体テスト プロジェクト]** を選択します。 それ以外の場合は、使用する単体テスト フレームワークのプロジェクト テンプレートを選択します。 この例の Accounts プロジェクトをテストするために、プロジェクトの名前を **AccountsTests** に設定します。

4.  単体テスト プロジェクトに、テスト対象のコードへの参照を追加します。  同じソリューションのコード プロジェクトへの参照を作成する方法は次のようになります。

    1.  **ソリューション エクスプローラー**でプロジェクトを選択します。

    2.  **[プロジェクト]** メニューの **[参照の追加]** をクリックします。

    3.  **[参照マネージャー]** ダイアログ ボックスで、**[ソリューション]** ノードを開き、**[プロジェクト]** を選択します。 コード プロジェクトの名前を選択し、ダイアログ ボックスを閉じます。

5.  テストするコードが別の場所にある場合、「[プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)」を参照してください。

## <a name="next-steps"></a>次の手順

 次のいずれかのセクションを参照してください。

**単体テストの記述**

- [コードの単体テスト](../test/unit-test-your-code.md)

- [C/C++ 用の単体テストの記述](writing-unit-tests-for-c-cpp.md)

- [単体テストでの MSTest フレームワークの使用](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**単体テストの実行**

- [テスト エクスプローラーを使用して単体テストを実行する](../test/run-unit-tests-with-test-explorer.md)