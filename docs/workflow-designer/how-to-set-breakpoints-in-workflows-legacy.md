---
title: "方法: ワークフロー内にブレークポイントを設定する (レガシ) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "ブレークポイント, ワークフローでの設定"
  - "ワークフローのデバッグ, ブレークポイントの設定"
  - "デバッグ, ワークフローでのブレークポイントの設定"
  - "ワークフロー, ブレークポイントの設定"
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 方法: ワークフロー内にブレークポイントを設定する (レガシ)
このトピックでは、従来の [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]を使用して作成された [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] アプリケーションでブレークポイントを設定する方法について説明します。[!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] アプリケーションが [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]を使用します。  
  
 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] の従来の[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]を使用して [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] アプリケーションを作成した場合、Visual Studio と同様に、ブレークポイントを C\# および Visual Basic コードで設定できます。設定したそれぞれのブレークポイントで、ワークフローの実行が停止します。  
  
 ブレークポイントには、*保留*、*バインド*、および*エラー*の 3 つの状態があります。ブレークポイントは設定時には「保留」になり、穴の空いた赤いアイコンで表示されます。特定の種類のワークフローがランタイムによって読み込まれると、「バインド」になり、穴のない赤いアイコンで表示されます。不適切な形式のブレークポイントを指定した場合 \(たとえばアクティビティ名が無効など\)、エラー ウィンドウが表示されます。ブレークポイントはブレークポイント ウィンドウに追加されますが、小さな x 印が付きます。  
  
 次のような方法で、ワークフロー デザイン サーフェイス上でアクティビティのブレークポイントを設定できます。  
  
-   アクティビティを右クリックして、**\[ブレークポイント\]** の \[ブレークポイントの挿入\] をクリックします。  
  
-   アクティビティを選択して、F9 キーを押します。  
  
-   **\[デバッグ\]** メニューの **\[ブレークポイントの作成\]** をクリックします。  
  
     また、このオプションを使用して、デバッグ中にデバッガがブレークポイントで停止したときに新しいブレークポイントを設定することもできます。  
  
    > [!NOTE]
    >  呼び出されるワークフローに対してブレークポイントを設定することはできません。  
  
### \[デバッグ\] メニューの \[ブレークポイントの作成\] オプションを使ってブレークポイントを設定するには  
  
1.  **\[デバッグ\]** メニューの **\[ブレークポイントの作成\]** をクリックします。  
  
2.  **\[関数でブレーク\]** をクリックします。  
  
     **\[ブレークポイントの作成\]** ダイアログ ボックスが表示されます。  
  
3.  **\[関数\]** テキスト ボックスで、アクティビティの名前を指定します。構文は `QualifiedActivityId[:[FullClassName][:InstanceId]]` です。  
  
    > [!NOTE]
    >  あるいは、**\[関数\]** テキスト ボックスでアクティビティ名を指定するのではなく、ワークフロー アクティビティの絶対パスを指定してブレークポイントを設定することもできます。たとえば、**WorkflowConsoleApplication1** という名前のワークフロー ソリューションがあり、**Delay1** というアクティビティを使用する **Workflow1** というワークフローがソリューション内にあるとします。この場合、アクティビティ名 **Delay1** を使用するか、パス **Delay1:WorkflowConsoleApplication1.Workflow1** または **Delay1:WorkflowConsoleApplication1.Workflow1:{6614886A\-608E\-412B\-BF98\-99FF1559DDDF}** を指定することができます。  
  
4.  関数名を検証するには、**\[関数名の確認に IntelliSense を使用する\]** チェック ボックスをオンにします。  
  
     このチェック ボックスをオンにしない場合、ブレークポイント名は検証されません。  
  
5.  **\[言語\]** リストから **\[ワークフロー\]** を選択します。  
  
6.  **\[OK\]** をクリックします。  
  
## 参照  
 [従来のワークフローのデバッグ](../workflow-designer/debugging-legacy-workflows.md)   
 [Visual Studio Debugger for Windows Workflow Foundation の起動 \(レガシ\)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)