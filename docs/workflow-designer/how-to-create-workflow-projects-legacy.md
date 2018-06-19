---
title: 'ワークフロー デザイナー - 方法: ワークフロー プロジェクト (レガシ) の作成'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb5d58c6d450a5e68d804e33785ec76349bfb6d8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973341"
---
# <a name="how-to-create-workflow-projects-legacy"></a>方法: ワークフロー プロジェクトを作成する (レガシ)

次の手順を .NET Framework version 3.5、または、WinFX を対象とする Windows Workflow Foundation (WF) プロジェクトを作成します。 この手順では、Visual Studio 2010 で提供される従来の Windows ワークフロー デザイナーを使用します。

## <a name="to-create-a-workflow-project"></a>ワークフロー プロジェクトを作成するには

1.  Visual Studio を起動します。

2.  **[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** を選択します。

     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

3.  いずれかを選択、 **.NET Framework 3.0**オプションまたは **.NET Framework 3.5**オプションで、ドロップダウン リストの上部にある、**新しいプロジェクト**従来のデザイナーにアクセスするウィンドウです。

    > [!NOTE]
    > Visual Studio 2010 の既定のオプションは **.NET Framework 4**です。 アプリケーションを作成する Windows Workflow Foundation (WF) をターゲットとする .NET Framework 4 は、このオプションが使用され、従来のデザイナーは使用されません。

4.  **プロジェクトの種類**] ウィンドウで、Visual c# プロジェクトまたは Visual Basic プロジェクトを選択し、[**ワークフロー**です。

5.  **テンプレート** ウィンドウで、インストールされているプロジェクト テンプレートのいずれかを選択します。

    -   シーケンシャル ワークフロー コンソール アプリケーション

    -   シーケンシャル ワークフロー ライブラリ

    -   ワークフロー アクティビティ ライブラリ

    -   ステート マシンのワークフロー コンソール アプリケーション

    -   ステート マシンのワークフロー ライブラリ

    -   空のワークフロー プロジェクト

6.  **名前**を識別しやすくようにプロジェクトのわかりやすい名前を入力します。

7.  **場所**ボックスで、プロジェクトを保存ディレクトリを入力**参照**ディレクトリに移動します。

     ソリューション ディレクトリをプロジェクトの作成を実行する場合に、選択、**ソリューションのディレクトリを作成**チェック ボックスをオンおよびに名前を入力、**ソリューション名**ボックス。

8.  **[OK]** をクリックします。

## <a name="see-also"></a>関連項目

- [従来のワークフロー プロジェクトの作成](../workflow-designer/creating-legacy-workflow-projects.md)