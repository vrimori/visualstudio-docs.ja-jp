---
title: "方法: ワークフロー (レガシ) 内のブレークポイントを設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- breakpoints, setting in workflows
- debugging, setting breakpoints in workflows
- debugging workflows, setting breakpoints
- workflows, setting breakpoints
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 89189feb32d84db8fb5c5eb7970faf325be1acd6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>方法: ワークフロー内にブレークポイントを設定する (レガシ)
このトピックでは、従来の [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]を使用して作成された [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] アプリケーションでブレークポイントを設定する方法について説明します。 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] アプリケーションが [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] または [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]を使用します。  
  
 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] の従来の[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]を使用して [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] アプリケーションを作成した場合、Visual Studio と同様に、ブレークポイントを C# および Visual Basic コードで設定できます。 設定したそれぞれのブレークポイントで、ワークフローの実行が停止します。  
  
 ブレークポイントが 3 つの状態:*保留*、*バインド*、および*エラー*です。 ブレークポイントは設定時には「保留」になり、穴の空いた赤いアイコンで表示されます。 特定の種類のワークフローがランタイムによって読み込まれると、「バインド」になり、穴のない赤いアイコンで表示されます。 不適切な形式のブレークポイントを指定した場合 (たとえばアクティビティ名が無効など)、エラー ウィンドウが表示されます。 ブレークポイントはブレークポイント ウィンドウに追加されますが、小さな x 印が付きます。  
  
 次のような方法で、ワークフロー デザイン サーフェイス上でアクティビティのブレークポイントを設定できます。  
  
-   アクティビティを右クリックし **ブレークポイント \ ブレークポイントの挿入**です。  
  
-   アクティビティを選択して、F9 キーを押します。  
  
-   選択**新しいブレークポイント**から、**デバッグ**メニュー。  
  
     また、このオプションを使用して、デバッグ中にデバッガがブレークポイントで停止したときに新しいブレークポイントを設定することもできます。  
  
    > [!NOTE]
    >  呼び出されるワークフローに対してブレークポイントを設定することはできません。  
  
### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>[デバッグ] メニューの [ブレークポイントの作成] オプションを使ってブレークポイントを設定するには  
  
1.  **デバッグ**メニューの **新しいブレークポイント**です。  
  
2.  をクリックして**関数でブレーク**です。  
  
     **新しいブレークポイント** ダイアログ ボックスが表示されます。  
  
3.  内のアクティビティの名前を指定、**関数**この構文を使用してテキスト ボックス:`QualifiedActivityId[:[FullClassName][:InstanceId]]`です。  
  
    > [!NOTE]
    >  アクティビティ名を使用する代わりに、必要に応じて、**関数**テキスト ボックスで、ワークフロー アクティビティの絶対パスを指定してブレークポイントを設定することができます。 たとえば、という名前のワークフロー ソリューション**WorkflowConsoleApplication1**という名前のソリューション内のワークフローと**Workflow1**アクティビティを使用すると呼ばれる**Delay1**. アクティビティ名を使用する**Delay1**とパスを指定または**delay1:workflowconsoleapplication1.workflow1:**または**delay1:workflowconsoleapplication1.workflow1:: {6614886A-608E-412B-BF98-99FF1559DDDF}**です。  
  
4.  選択、 **IntelliSense を使用する**関数名を検証する チェック ボックスです。  
  
     このチェック ボックスをオンにしない場合、ブレークポイント名は検証されません。  
  
5.  選択**ワークフロー**から、**言語** ボックスの一覧です。  
  
6.  **[OK]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [従来のワークフローのデバッグ](../workflow-designer/debugging-legacy-workflows.md)   
 [Visual Studio Debugger for Windows Workflow Foundation の起動 (レガシ)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)