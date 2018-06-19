---
title: 'ワークフロー デザイナー - 方法: アクティビティ デザイナー ライブラリを作成します。'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d05ddb48e88627f4b7ab4112c164b5129ddba910
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974592"
---
# <a name="how-to-create-an-activity-designer-library"></a>アクティビティ デザイナー ライブラリを作成する方法
カスタム アクティビティ デザイナーを使用して、標準アクティビティやカスタム アクティビティのためのユーザー インターフェイスを作成できます。 ユーザー インターフェイスが複雑にならないようにして、1 つのアクティビティに対応するアクティビティ デザイナーを複数作成することができます。 このシナリオでは、複数の対象に対応したデザイナーを作成できます。

## <a name="to-create-an-activity-designer-library"></a>アクティビティ デザイナー ライブラリを作成するには

1.  Visual Studio 2010 を起動します。

2.  **ファイル** メニューのをポイント**新規**、し、**プロジェクト**を開くには、**新しいプロジェクト** ダイアログ ボックス。

3.  **プロジェクトの種類**ペインで、**ワークフロー**いずれかから、 **Visual c#** または**Visual Basic**優先によってグループ化言語。

4.  **テンプレート**ペインで、**アクティビティ デザイナー ライブラリ**です。

5.  **名前**を識別しやすくようにプロジェクトのわかりやすい名前を入力します。

6.  **場所**ボックスで、プロジェクトを保存ディレクトリを入力**参照**まで移動します。

7.  **ソリューション**ボックスに、ソリューションのわかりやすい名前を入力し、をクリックして**OK**です。

    > [!NOTE]
    > ワークフロー コンソール アプリケーションを既存のソリューションに追加する場合は、Visual Studio 2010 でそのソリューションを開きでソリューションを右クリックして**ソリューション エクスプ ローラー**を選択し、**追加**、し、 **新しいプロジェクト**を開くには、**新しいプロジェクト** ダイアログ ボックス。 上記の手順を実行します。

8.  プロジェクト テンプレートにより、アクティビティ デザイナー定義が XAML で作成され、ソース コード内に分離コード実装ファイルが作成されます。 Windows ワークフロー デザイナーが開き、アクティビティ デザイナーのキャンバスが表示されます。

9. ドラッグ Windows Presentation Foundation (WPF) コントロール、**ツールボックス**カスタム アクティビティ デザイナーで使用するデザイン サーフェイスにします。  カスタム アクティビティ デザイナーを実装する方法の例は、次を参照してください。[する方法: カスタム アクティビティ デザイナーを作成する](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer)です。

    > [!WARNING]
    > カスタム アクティビティ デザイナーは、既定の .NET Framework 4activities だけカスタム アクティビティにも使用できます。

## <a name="see-also"></a>関連項目

- [ワークフロー プロジェクトの作成](../workflow-designer/creating-a-workflow-project.md)