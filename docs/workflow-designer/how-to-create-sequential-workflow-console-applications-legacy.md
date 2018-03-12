---
title: "方法: シーケンシャル ワークフロー コンソール アプリケーション (レガシ) を作成 |Microsoft ドキュメント"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 211c750dd0baa1dad0a365310b3636c0d0922882
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>方法: シーケンシャル ワークフロー コンソール アプリケーションを作成する (レガシ)
によって提供される従来の Windows ワークフロー デザイナーを使用してシーケンシャル ワークフロー コンソール アプリケーション プロジェクトを作成する次の手順に従って[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]です。 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] または [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]を使用します。

### <a name="to-create-a-sequential-workflow-console-application"></a>シーケンシャル ワークフロー コンソール アプリケーションを作成するには

1.  Visual Studio を起動します。

2.  **ファイル**] メニューのをポイント**新規**、し、[**プロジェクト**です。

     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

3.  いずれかを選択、 **.NET Framework 3.0**オプションまたは**.NET Framework 3.5**オプションで、ドロップダウン リストの上部にある、**新しいプロジェクト**従来のデザイナーにアクセスするウィンドウです。

    > [!NOTE]
    > 既定のオプションに[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]は**.NET Framework 4**です。 このオプションは、[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] を対象とする [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] アプリケーションを作成する場合に使用され、従来のデザイナーは使用しません。

4.  **プロジェクトの種類**ウィンドウ、Visual c# プロジェクトまたは Visual Basic プロジェクト (**他の言語**)、し、**ワークフロー**です。

5.  **テンプレート**ペインで、**シーケンシャル ワークフロー コンソール アプリケーション**です。

6.  **名前**を識別しやすくようにプロジェクトのわかりやすい名前を入力します。

7.  **場所**ボックスで、プロジェクトを保存ディレクトリを入力**参照**まで移動します。

     Windows フォーム デザイナが開き、作成済みプロジェクトの Form1 が表示されます。

8.  **[OK]**をクリックします。

     ワークフロー デザイナが開き、作成済みシーケンシャル ワークフローのワークフロー デザイン サーフェイスが表示されます。

9. アクティビティをドラッグして、**ツールボックス**でデザイン サーフェイスに、**アクティビティをドロップ**領域を指定します。

## <a name="see-also"></a>関連項目

- [従来のワークフロー プロジェクトの作成](../workflow-designer/creating-legacy-workflow-projects.md)
- [ワークフローの開発](http://msdn.microsoft.com/en-us/557bcb1f-a7ab-49f6-8df7-2706b7001301)