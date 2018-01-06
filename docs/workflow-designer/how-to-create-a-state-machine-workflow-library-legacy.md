---
title: "方法: ステート マシン ワークフロー ライブラリ (レガシ) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- projects, state machine workflow library
- state machine workflow libraries
- workflows, state machine workflow library
ms.assetid: 5bd68c6e-6a98-47d9-826d-9bb7a4fd72f8
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 73fe219a3047758f66dbff47e59031adb1de9258
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-state-machine-workflow-library-legacy"></a>方法: ステート マシン ワークフロー ライブラリを作成する (レガシ)
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] が備えている従来の [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]を使用してステート マシン ワークフロー ライブラリ プロジェクトを作成するには、次の手順を実行します。 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] または [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]を使用します。  
  
### <a name="to-create-a-state-machine-workflow-library-project"></a>ステート マシン ワークフロー ライブラリ プロジェクトを作成するには  
  
1.  Visual Studio を起動します。  
  
2.  **ファイル**] メニューのをポイント**新規**、し、[**プロジェクト**です。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
3.  いずれかを選択、 **.NET Framework 3.0**オプションまたは**.NET Framework 3.5**オプションで、ドロップダウン リストの上部にある、**新しいプロジェクト**従来のデザイナーにアクセスするウィンドウです。  
  
    > [!NOTE]
    >  既定のオプションに[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]は**.NET Framework 4**です。 このオプションは、[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] を対象とする [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] アプリケーションを作成する場合に使用され、従来のデザイナーは使用しません。  
  
4.  **プロジェクトの種類**ウィンドウで、Visual c# または Visual Basic (**他の言語**) し、**ワークフロー**です。  
  
5.  **テンプレート**ペインで、**ステート マシン ワークフロー ライブラリ**です。  
  
6.  **名前**を識別しやすくようにプロジェクトのわかりやすい名前を入力します。  
  
7.  **場所**ボックスで、プロジェクトを保存ディレクトリを入力**参照**まで移動します。  
  
     ソリューション ディレクトリをプロジェクトの作成を実行する場合に、選択、**ソリューションのディレクトリを作成**チェック ボックスをオンおよびに名前を入力、**ソリューション名**ボックス。  
  
8.  **[OK]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [従来のワークフロー プロジェクトを作成します。](../workflow-designer/creating-legacy-workflow-projects.md)   
 [ステート マシン ワークフロー](/dotnet/framework/windows-workflow-foundation/state-machine-workflows)