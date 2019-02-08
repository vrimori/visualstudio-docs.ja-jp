---
title: 単体テスト プロジェクトを作成する
ms.date: 01/29/2019
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 813829e1e4024a38415cd9cef6da9fa7ca2ed87b
ms.sourcegitcommit: 9866740aec05d1a3a5dc3b4b6d2ceaeecbd3fc29
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2019
ms.locfileid: "55424409"
---
# <a name="create-a-unit-test-project"></a>単体テスト プロジェクトを作成する

単体テストでは、多くの場合、テスト対象のコードの構造を再現します。 たとえば、製品のコード プロジェクトごとに単体テスト プロジェクトを作成します。 テスト プロジェクトは本稼働コードと同じソリューションに置くことも、別個のソリューションに置くこともできます。 1 つのソリューションに複数の単体テスト プロジェクトを置くこともできます。

> [!NOTE]
> ネイティブ コードの単体テストの場所とテスト プロジェクトの構造は、この記事の説明にある構造とは異なっていても構いません。 詳細については、「[C/C++ 用の単体テストの記述](writing-unit-tests-for-c-cpp.md)」を参照してください。

## <a name="to-create-a-unit-test-project"></a>単体テスト プロジェクトを作成するには

1. **[ファイル]** メニューの **[新規作成]** を選択し、**[プロジェクト]** を選択します。 または、**Ctrl** + **Shift** + **N** キーを押します。

2. **[新しいプロジェクト]** ダイアログ ボックスで、**[インストール済み]** ノードを展開して、テスト プロジェクトで使用する言語を選択し、**[テスト]** をクリックします。

3. Microsoft 単体テスト フレームワークの 1 つを使用するには、プロジェクト テンプレートの一覧から **[単体テスト プロジェクト]** を選択します。 それ以外の場合は、使用する単体テスト フレームワークのプロジェクト テンプレートを選択します。 プロジェクトに名前を付けて、**[OK]** を選択します。

4. 単体テスト プロジェクトに、テスト対象のコードへの参照を追加します。 同じソリューション内のコード プロジェクトへの参照を追加するには:

   1. **ソリューション エクスプローラー**でテスト プロジェクトを選択します。

   2. **[プロジェクト]** メニューの **[参照の追加]** をクリックします。

   3. **[参照マネージャー]** で、**[プロジェクト]** の下の **[ソリューション]** ノードを選択します。 テストするコード プロジェクトを選択して、**[OK]** を選択します。

   テストするコードが別の場所にある場合は、「[プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)」を参照してください。

## <a name="next-steps"></a>次の手順

次のいずれかのセクションを参照してください。

**単体テストの記述**

- [コードの単体テスト](../test/unit-test-your-code.md)

- [C/C++ 用の単体テストの記述](writing-unit-tests-for-c-cpp.md)

- [単体テストでの MSTest フレームワークの使用](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**単体テストの実行**

- [テスト エクスプローラーを使用して単体テストを実行する](../test/run-unit-tests-with-test-explorer.md)