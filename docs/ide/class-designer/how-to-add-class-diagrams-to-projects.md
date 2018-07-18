---
title: '方法: プロジェクトにクラス ダイアグラムを追加する (クラス デザイナー)'
ms.date: 05/08/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 94e13d4c1dbda200c2e2660e4b3b44e62ed99496
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "33998190"
---
# <a name="how-to-add-class-diagrams-to-projects"></a>方法: プロジェクトにクラス ダイアグラムを追加する

クラスおよび他の型の設計、編集およびリファクタリングを行うには、クラス ダイアグラムを C#、Visual Basic、または C++ プロジェクトに追加します。 プロジェクト内のコードの異なる部分を視覚化するには、複数のクラス ダイアグラムをプロジェクトに追加します。

複数のアプリでコードを共有しているプロジェクトからは、クラス ダイアグラムを作成できません。 UML クラス ダイアグラムを作成するには、「[UML モデリング プロジェクトおよびダイアグラムを作成する](../../modeling/create-uml-modeling-projects-and-diagrams.md)」を参照してください。

## <a name="install-the-class-designer-component"></a>クラス デザイナー コンポーネントのインストール

Visual Studio 2017 を実行していて、**クラス デザイナー** コンポーネントをインストールしていない場合は、以下の手順に従ってインストールします。

1. **Visual Studio インストーラー**を開くには、Windows の [スタート] メニューから、または Visual Studio のメニュー バーから **[ツール]** > **[ツールと機能を取得]** を選択します。

   **Visual Studio インストーラー**が開きます。

1. **[個々のコンポーネント]** タブを選択し、**[コード ツール]** カテゴリまで下にスクロールします。

1. **[クラス デザイナー]**、**[変更]** の順に選択します。

   ![Visual Studio インストーラーでのクラス デザイナー コンポーネント](media/class-designer-component.png)

   **クラス デザイナー** コンポーネントのインストールが開始します。

## <a name="add-a-blank-class-diagram-to-a-project"></a>プロジェクトに空のクラス ダイアグラムを追加する

1. **ソリューション エクスプローラー**で、プロジェクト ノードを右クリックし、**[追加]** > **[新しい項目]** の順に選択します。 または、**Ctrl**+**Shift**+**A** キーを押します。

   **[新しい項目の追加]** ダイアログが開きます。

2. **[共通項目]** > **[全般]** の順に展開してから、テンプレートの一覧から **[クラス ダイアグラム]** を選択します。 Visual C++ プロジェクトの場合は、**[ユーティリティ]** カテゴリで**クラス ダイアグラム** テンプレートを見つけます。

   > [!NOTE]
   > **クラス ダイアグラム** テンプレートが表示されない場合は、[この手順に従って](#install-the-class-designer-component)、Visual Studio 用の**クラス デザイナー** コンポーネントをインストールします。

   クラス デザイナーでクラス ダイアグラムが開き、**ソリューション エクスプローラー**に *.cd* 拡張子付きのファイルとして表示されます。 **[ツールボックス]** からダイアグラムに図形と線をドラッグできます。

複数のクラス ダイアグラムを追加するには、この手順を繰り返します。

## <a name="add-a-class-diagram-based-on-existing-types"></a>既存の型に基づいてクラス ダイアグラムを追加する

**ソリューション エクスプローラー**で、クラス ファイル コンテキスト メニューを開き、**[クラス ダイアグラムの表示]** を選択します。

- または -

**[クラス ビュー]** で、名前空間または型のコンテキスト メニューを開き、**[クラス ダイアグラムで表示]** を選択します。

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>クラス ダイアグラムに完全なプロジェクトの内容を表示するには

**ソリューション エクスプローラー**またはクラス ビューで、プロジェクトを右クリックし、**[表示]** を選択してから **[クラス ダイアグラムの表示]** を選択します。

自動設定されたクラス ダイアグラムが作成されます。

## <a name="see-also"></a>関連項目

- [方法: クラス デザイナーを使用して型を作成する](how-to-create-types.md)
- [方法: 既存の型を表示する](how-to-view-existing-types.md)
- [クラスと型の設計と表示](designing-and-viewing-classes-and-types.md)
- [型およびリレーションシップの表示](viewing-types-and-relationships.md)
- [クラス ダイアグラムの使用](working-with-class-diagrams.md)
