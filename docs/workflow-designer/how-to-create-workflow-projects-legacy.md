---
title: '方法: ワークフロー プロジェクト (レガシ) を作成 |Microsoft ドキュメント'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ca6fdbbd8a744c472c06fdefbdafce77679ec2c9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-workflow-projects-legacy"></a>方法: ワークフロー プロジェクトを作成する (レガシ)
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] または [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] を対象とする [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] プロジェクトを作成するには、次の手順を実行します。 この手順では、レガシ Windows ワークフロー デザイナーによって提供される[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]です。

### <a name="to-create-a-workflow-project"></a>ワークフロー プロジェクトを作成するには

1.  [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] を起動します。

2.  **[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** を選択します。

     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

3.  いずれかを選択、 **.NET Framework 3.0**オプションまたは**.NET Framework 3.5**オプションで、ドロップダウン リストの上部にある、**新しいプロジェクト**従来のデザイナーにアクセスするウィンドウです。

    > [!NOTE]
    > 既定のオプションに[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]は**.NET Framework 4**です。 このオプションは、[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] を対象とする [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] アプリケーションを作成する場合に使用され、従来のデザイナーは使用しません。

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

8.  **[OK]**をクリックします。

## <a name="see-also"></a>関連項目

- [従来のワークフロー プロジェクトの作成](../workflow-designer/creating-legacy-workflow-projects.md)