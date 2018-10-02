---
title: '方法: ワークフロー (レガシ) にブレークポイントを設定 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- breakpoints, setting in workflows
- debugging, setting breakpoints in workflows
- debugging workflows, setting breakpoints
- workflows, setting breakpoints
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: ac587b238d52e8955a4fe70cabc89444b39c712d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537403"
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>方法: ワークフロー内にブレークポイントを設定する (レガシ)
このトピックでは、従来の [!INCLUDE[wf](../includes/wf-md.md)]を使用して作成された [!INCLUDE[wfd1](../includes/wfd1-md.md)] アプリケーションでブレークポイントを設定する方法について説明します。 [!INCLUDE[wfd2](../includes/wfd2-md.md)] アプリケーションが [!INCLUDE[wf2](../includes/wf2-md.md)] または [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]を使用します。  
  
 [!INCLUDE[wfd2](../includes/wfd2-md.md)] の従来の[!INCLUDE[vs2010](../includes/vs2010-md.md)]を使用して [!INCLUDE[wf2](../includes/wf2-md.md)] アプリケーションを作成した場合、Visual Studio と同様に、ブレークポイントを C# および Visual Basic コードで設定できます。 設定したそれぞれのブレークポイントで、ワークフローの実行が停止します。  
  
 ブレークポイントが 3 つの状態:*保留*、*バインド*、および*エラー*します。 ブレークポイントは設定時には「保留」になり、穴の空いた赤いアイコンで表示されます。 特定の種類のワークフローがランタイムによって読み込まれると、「バインド」になり、穴のない赤いアイコンで表示されます。 不適切な形式のブレークポイントを指定した場合 (たとえばアクティビティ名が無効など)、エラー ウィンドウが表示されます。 ブレークポイントはブレークポイント ウィンドウに追加されますが、小さな x 印が付きます。  
  
 次のような方法で、ワークフロー デザイン サーフェイス上でアクティビティのブレークポイントを設定できます。  
  
-   アクティビティを右クリックして**ブレークポイント \ ブレークポイントの挿入**します。  
  
-   アクティビティを選択して、F9 キーを押します。  
  
-   選択**新しいブレークポイント**から、**デバッグ**メニュー。  
  
     また、このオプションを使用して、デバッグ中にデバッガがブレークポイントで停止したときに新しいブレークポイントを設定することもできます。  
  
    > [!NOTE]
    >  呼び出されるワークフローに対してブレークポイントを設定することはできません。  
  
### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>[デバッグ] メニューの [ブレークポイントの作成] オプションを使ってブレークポイントを設定するには  
  
1.  **デバッグ**メニューの **新しいブレークポイント**します。  
  
2.  クリックして**関数でブレーク**します。  
  
     **新しいブレークポイント** ダイアログ ボックスが表示されます。  
  
3.  内のアクティビティの名前を指定、**関数**この構文を使用してテキスト ボックス:`QualifiedActivityId[:[FullClassName][:InstanceId]]`します。  
  
    > [!NOTE]
    >  アクティビティ名を使用する代わりに、必要に応じて、**関数**テキスト ボックスに、ワークフロー アクティビティの絶対パスを指定してブレークポイントを設定することができます。 たとえば、という名前のワークフロー ソリューション**WorkflowConsoleApplication1**という名前のソリューションでのワークフローと**Workflow1**というアクティビティを使用する**Delay1**. アクティビティ名を使用する**Delay1**としてパスを指定または**Delay1:WorkflowConsoleApplication1.Workflow1**または**Delay1:WorkflowConsoleApplication1.Workflow1: {6614886A-608E-412B-BF98-99FF1559DDDF}** します。  
  
4.  選択、 **IntelliSense を使用する**関数名を検証する チェック ボックス。  
  
     このチェック ボックスをオンにしない場合、ブレークポイント名は検証されません。  
  
5.  選択**ワークフロー**から、**言語**一覧。  
  
6.  **[OK]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [従来のワークフローのデバッグ](../workflow-designer/debugging-legacy-workflows.md)   
 [Visual Studio Debugger for Windows Workflow Foundation の起動 (レガシ)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)