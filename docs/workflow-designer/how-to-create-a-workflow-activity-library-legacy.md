---
title: 'ワークフロー デザイナー - 方法: ワークフロー アクティビティ ライブラリ (レガシ) を作成します。'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, activity library projects
- workflow activity libraries
- projects, workflow activity libraries
ms.assetid: fb5aa940-2ae8-4b52-b52c-51c20861a7b4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 432766e60ee1384db0f8cd5bad1f369e80ddd20a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-workflow-activity-library-legacy"></a>方法: ワークフロー アクティビティ ライブラリを作成する (レガシ)

Visual Studio 2010 で従来の Windows ワークフロー デザイナーを使用して、ワークフロー アクティビティ ライブラリ プロジェクトを作成する手順に従います。 .NET Framework version 3.5、または、WinFX を対象とする必要がある場合は、従来のワークフロー デザイナーを使用します。

## <a name="to-create-a-workflow-activity-library-project"></a>ワークフロー アクティビティ ライブラリ プロジェクトを作成するには

1.  Visual Studio を起動します。

2.  **[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** を選択します。

     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

3.  いずれかを選択、 **.NET Framework 3.0**オプションまたは **.NET Framework 3.5**オプションで、ドロップダウン リストの上部にある、**新しいプロジェクト**従来のデザイナーにアクセスするウィンドウです。

    > [!NOTE]
    > Visual Studio 2010 の既定のオプションは **.NET Framework 4**です。 アプリケーションを作成する Windows Workflow Foundation (WF) をターゲットとする .NET Framework 4 は、このオプションが使用され、従来のデザイナーは使用されません。

4.  **プロジェクトの種類**ウィンドウで、Visual c# または Visual Basic (**他の言語**) し、**ワークフロー**です。

5.  **テンプレート**ペインで、 **Workflow Activity Library**です。

6.  **名前**を識別しやすくようにプロジェクトのわかりやすい名前を入力します。

7.  **場所**ボックスで、プロジェクトを保存ディレクトリを入力**参照**まで移動します。

     ソリューション ディレクトリをプロジェクトの作成を実行する場合に、選択、**ソリューションのディレクトリを作成**チェック ボックスをオンおよびに名前を入力、**ソリューション名**ボックス。

8.  **[OK]** をクリックします。

## <a name="see-also"></a>関連項目

- [従来のワークフロー プロジェクトの作成](../workflow-designer/creating-legacy-workflow-projects.md)
- [従来のアクティビティ デザイナーの使用](../workflow-designer/using-the-legacy-activity-designer.md)
- [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)
- [ワークフロー活動の開発](http://msdn.microsoft.com/en-us/19876dfc-dfa5-4d52-b1f5-1d087474cc52)
- [Windows Workflow Foundation アクティビティ](http://msdn.microsoft.com/en-us/192c4c1e-afb6-4f58-ab11-2b5bbbc2d2c0)