---
title: 'ワークフロー デザイナー - 方法: シーケンシャル ワークフロー ライブラリ (レガシ) を作成します。'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- sequential workflows, creating library
- workflows, sequential workflow library
- projects, sequential workflow library
- sequential workflow libraries
ms.assetid: 9433ccf3-1eab-4d53-90ff-2e7b2341676c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2ed341481ec3e82165a9f4cefd71eb362781d96c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-sequential-workflow-library-legacy"></a>方法: シーケンシャル ワークフロー ライブラリを作成する (レガシ)

Visual Studio 2010 で従来の Windows ワークフロー デザイナーを使用してシーケンシャル ワークフロー ライブラリ プロジェクトを作成する手順に従います。 .NET Framework version 3.5、または、WinFX を対象とする必要がある場合は、従来のワークフロー デザイナーを使用します。

## <a name="to-create-a-sequential-workflow-library-project"></a>シーケンシャル ワークフロー ライブラリ プロジェクトを作成するには

1.  Visual Studio を起動します。

2.  **[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** を選択します。

     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

3.  いずれかを選択、 **.NET Framework 3.0**オプションまたは **.NET Framework 3.5**オプションで、ドロップダウン リストの上部にある、**新しいプロジェクト**従来のデザイナーにアクセスするウィンドウです。

    > [!NOTE]
    > Visual Studio 2010 の既定のオプションは **.NET Framework 4**です。 アプリケーションを作成する Windows Workflow Foundation (WF) をターゲットとする .NET Framework 4 は、このオプションが使用され、従来のデザイナーは使用されません。

4.  **プロジェクトの種類**ウィンドウで、Visual c# または Visual Basic (**他の言語**)、し、**ワークフロー**です。

5.  **テンプレート**ペインで、**シーケンシャル ワークフロー ライブラリ**です。

6.  **名前**を識別しやすくようにプロジェクトのわかりやすい名前を入力します。

7.  **場所**ボックスで、プロジェクトを保存ディレクトリを入力**参照**まで移動します。

     ソリューション ディレクトリをプロジェクトの作成を実行する場合に、選択、**ソリューションのディレクトリを作成**チェック ボックスをオンおよびに名前を入力、**ソリューション名**ボックス。

8.  **[OK]** をクリックします。

## <a name="see-also"></a>関連項目

- [従来のワークフロー プロジェクトの作成](../workflow-designer/creating-legacy-workflow-projects.md)
- [ワークフローの作成スタイル](http://msdn.microsoft.com/en-us/aacf4ec6-da05-4974-958a-974769dda739)