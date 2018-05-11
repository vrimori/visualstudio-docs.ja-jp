---
title: 'ワークフロー デザイナー - 方法: シーケンシャル ワークフロー コンソール アプリケーション (レガシ) を作成します。'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb4e048fdf8eb8fee541f84656a29427b5a07a1d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>方法: シーケンシャル ワークフロー コンソール アプリケーションを作成する (レガシ)

Visual Studio 2010 で従来の Windows ワークフロー デザイナーを使用してシーケンシャル ワークフロー コンソール アプリケーション プロジェクトを作成する手順に従います。 .NET Framework version 3.5、または、WinFX を対象とする必要がある場合は、従来のワークフロー デザイナーを使用します。

## <a name="to-create-a-sequential-workflow-console-application"></a>シーケンシャル ワークフロー コンソール アプリケーションを作成するには

1.  Visual Studio を起動します。

2.  **[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** を選択します。

     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

3.  いずれかを選択、 **.NET Framework 3.0**オプションまたは **.NET Framework 3.5**オプションで、ドロップダウン リストの上部にある、**新しいプロジェクト**従来のデザイナーにアクセスするウィンドウです。

    > [!NOTE]
    > Visual Studio 2010 の既定のオプションは **.NET Framework 4**です。 アプリケーションを作成する Windows Workflow Foundation (WF) をターゲットとする .NET Framework 4 は、このオプションが使用され、従来のデザイナーは使用されません。

4.  **プロジェクトの種類**ウィンドウ、Visual c# プロジェクトまたは Visual Basic プロジェクト (**他の言語**)、し、**ワークフロー**です。

5.  **テンプレート**ペインで、**シーケンシャル ワークフロー コンソール アプリケーション**です。

6.  **名前**を識別しやすくようにプロジェクトのわかりやすい名前を入力します。

7.  **場所**ボックスで、プロジェクトを保存ディレクトリを入力**参照**まで移動します。

     Windows フォーム デザイナが開き、作成済みプロジェクトの Form1 が表示されます。

8.  **[OK]** をクリックします。

     ワークフロー デザイナが開き、作成済みシーケンシャル ワークフローのワークフロー デザイン サーフェイスが表示されます。

9. アクティビティをドラッグして、**ツールボックス**でデザイン サーフェイスに、**アクティビティをドロップ**領域を指定します。

## <a name="see-also"></a>関連項目

- [従来のワークフロー プロジェクトの作成](../workflow-designer/creating-legacy-workflow-projects.md)
- [ワークフローの開発](http://msdn.microsoft.com/en-us/557bcb1f-a7ab-49f6-8df7-2706b7001301)