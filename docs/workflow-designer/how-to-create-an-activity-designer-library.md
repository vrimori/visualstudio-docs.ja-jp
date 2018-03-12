---
title: "方法: アクティビティ デザイナー ライブラリを作成 |Microsoft ドキュメント"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0f257aabb4b1c2c1b1dce05e34273dc303a8f7da
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-create-an-activity-designer-library"></a>アクティビティ デザイナー ライブラリを作成する方法
カスタム アクティビティ デザイナーを使用して、標準アクティビティやカスタム アクティビティのためのユーザー インターフェイスを作成できます。 ユーザー インターフェイスが複雑にならないようにして、1 つのアクティビティに対応するアクティビティ デザイナーを複数作成することができます。 このシナリオでは、複数の対象に対応したデザイナーを作成できます。

### <a name="to-create-an-activity-designer-library"></a>アクティビティ デザイナー ライブラリを作成するには

1.  [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] を起動します。

2.  **ファイル** メニューのをポイント**新規**、し、**プロジェクト.**を開くには、**新しいプロジェクト** ダイアログ ボックス。

3.  **プロジェクトの種類**ペインで、**ワークフロー**いずれかから、 **Visual c#**または**Visual Basic**優先によってグループ化言語。

4.  **テンプレート**ペインで、**アクティビティ デザイナー ライブラリ**です。

5.  **名前**を識別しやすくようにプロジェクトのわかりやすい名前を入力します。

6.  **場所**ボックスで、プロジェクトを保存ディレクトリを入力**参照**まで移動します。

7.  **ソリューション**ボックスに、ソリューションのわかりやすい名前を入力し、をクリックして**OK**です。

    > [!NOTE]
    > ワークフロー コンソール アプリケーションを既存のソリューションに追加する場合でそのソリューションを開きます[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]でソリューションを右クリックして**ソリューション エクスプ ローラー**を選択し、**追加**、し、 **新しいプロジェクト.**を開くには、**新しいプロジェクト** ダイアログ ボックス。 上記の手順を実行します。

8.  プロジェクト テンプレートにより、アクティビティ デザイナー定義が XAML で作成され、ソース コード内に分離コード実装ファイルが作成されます。 Windows ワークフロー デザイナーが開き、アクティビティ デザイナーのキャンバスが表示されます。

9. ドラッグ[!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)]から制御、**ツールボックス**カスタム アクティビティ デザイナーで使用するデザイン サーフェイスにします。  カスタム アクティビティ デザイナーを実装する方法の例は、次を参照してください。[する方法: カスタム アクティビティ デザイナーを作成する](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer)です。

    > [!WARNING]
    > カスタム アクティビティ デザイナーは、既定とカスタム アクティビティにも使用できます[!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)]アクティビティ。

## <a name="see-also"></a>関連項目

- [ワークフロー プロジェクトの作成](../workflow-designer/creating-a-workflow-project.md)