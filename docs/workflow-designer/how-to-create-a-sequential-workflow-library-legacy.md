---
title: "方法: シーケンシャル ワークフロー ライブラリ (レガシ) を作成 |Microsoft ドキュメント"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- sequential workflows, creating library
- workflows, sequential workflow library
- projects, sequential workflow library
- sequential workflow libraries
ms.assetid: 9433ccf3-1eab-4d53-90ff-2e7b2341676c
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 165f63bec8fea7ec23b7e919d0f5e6c050b9ad6d
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-create-a-sequential-workflow-library-legacy"></a>方法: シーケンシャル ワークフロー ライブラリを作成する (レガシ)

によって提供される従来の Windows ワークフロー デザイナーを使用してシーケンシャル ワークフロー ライブラリ プロジェクトを作成する次の手順に従って[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]です。 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] または [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]を使用します。

### <a name="to-create-a-sequential-workflow-library-project"></a>シーケンシャル ワークフロー ライブラリ プロジェクトを作成するには

1.  Visual Studio を起動します。

2.  **ファイル**] メニューのをポイント**新規**、し、[**プロジェクト**です。

     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

3.  いずれかを選択、 **.NET Framework 3.0**オプションまたは**.NET Framework 3.5**オプションで、ドロップダウン リストの上部にある、**新しいプロジェクト**従来のデザイナーにアクセスするウィンドウです。

    > [!NOTE]
    > 既定のオプションに[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]は**.NET Framework 4**です。 このオプションは、[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] を対象とする [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] アプリケーションを作成する場合に使用され、従来のデザイナーは使用しません。

4.  **プロジェクトの種類**ウィンドウで、Visual c# または Visual Basic (**他の言語**)、し、**ワークフロー**です。

5.  **テンプレート**ペインで、**シーケンシャル ワークフロー ライブラリ**です。

6.  **名前**を識別しやすくようにプロジェクトのわかりやすい名前を入力します。

7.  **場所**ボックスで、プロジェクトを保存ディレクトリを入力**参照**まで移動します。

     ソリューション ディレクトリをプロジェクトの作成を実行する場合に、選択、**ソリューションのディレクトリを作成**チェック ボックスをオンおよびに名前を入力、**ソリューション名**ボックス。

8.  **[OK]**をクリックします。

## <a name="see-also"></a>関連項目

- [従来のワークフロー プロジェクトの作成](../workflow-designer/creating-legacy-workflow-projects.md)
- [ワークフローの作成スタイル](http://msdn.microsoft.com/en-us/aacf4ec6-da05-4974-958a-974769dda739)