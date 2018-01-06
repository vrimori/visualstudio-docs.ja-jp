---
title: "方法: シーケンシャル ワークフロー コンソール アプリケーション (レガシ) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 79969572e4cab24e93a6c593a23369a00243ae0e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>方法: シーケンシャル ワークフロー コンソール アプリケーションを作成する (レガシ)
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] が備えている従来の [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]を使用してシーケンシャル ワークフロー コンソール アプリケーション プロジェクトを作成するには、次の手順を実行します。 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] または [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]を使用します。  
  
### <a name="to-create-a-sequential-workflow-console-application"></a>シーケンシャル ワークフロー コンソール アプリケーションを作成するには  
  
1.  Visual Studio を起動します。  
  
2.  **ファイル**] メニューのをポイント**新規**、し、[**プロジェクト**です。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
3.  いずれかを選択、 **.NET Framework 3.0**オプションまたは**.NET Framework 3.5**オプションで、ドロップダウン リストの上部にある、**新しいプロジェクト**従来のデザイナーにアクセスするウィンドウです。  
  
    > [!NOTE]
    >  既定のオプションに[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]は**.NET Framework 4**です。 このオプションは、[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] を対象とする [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] アプリケーションを作成する場合に使用され、従来のデザイナーは使用しません。  
  
4.  **プロジェクトの種類**ウィンドウ、Visual c# プロジェクトまたは Visual Basic プロジェクト (**他の言語**)、し、**ワークフロー**です。  
  
5.  **テンプレート**ペインで、**シーケンシャル ワークフロー コンソール アプリケーション**です。  
  
6.  **名前**を識別しやすくようにプロジェクトのわかりやすい名前を入力します。  
  
7.  **場所**ボックスで、プロジェクトを保存ディレクトリを入力**参照**まで移動します。  
  
     Windows フォーム デザイナが開き、作成済みプロジェクトの Form1 が表示されます。  
  
8.  **[OK]**をクリックします。  
  
     ワークフロー デザイナが開き、作成済みシーケンシャル ワークフローのワークフロー デザイン サーフェイスが表示されます。  
  
9. アクティビティをドラッグして、**ツールボックス**でデザイン サーフェイスに、**アクティビティをドロップ**領域を指定します。  
  
## <a name="see-also"></a>参照  
 [従来のワークフロー プロジェクトを作成します。](../workflow-designer/creating-legacy-workflow-projects.md)   
 [ワークフローの開発](http://msdn.microsoft.com/en-us/557bcb1f-a7ab-49f6-8df7-2706b7001301)