---
title: "従来のワークフロー デザイナーの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Visual Studio 2005 Extensions for Windows Workflow Foundation, 概要"
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
caps.latest.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# 従来のワークフロー デザイナーの使用
[!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] が備えている従来の[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]を使用すると、[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象とすることができます。  
  
 従来のワークフロー デザイナーにアクセスするには、**\[新しいプロジェクト\]** ウィンドウの上部にあるドロップダウン リストで **\[.NET Framework 3.0\]** オプションまたは **\[.NET Framework 3.5\]** オプションを選択します。[!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] での既定のオプションは **\[.NET Framework 4\]** です。このオプションは、[!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] を対象とする [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] アプリケーションを作成する場合に使用されます。  
  
 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] で、使い慣れた [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ユーザー インターフェイスを使用して [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] アプリケーションをグラフィカルに作成できます。[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] アプリケーションは、アクティビティと呼ばれるワークフロー プロセス ステップで構成されます。ワークフローを作成するには、それぞれのアクティビティ デザイナーを **\[ツールボックス\]** からデザイン サーフェイスにドラッグして、デザイン サーフェイス上にアクティビティを作成します。  
  
 次の表に、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] for Windows Workflow Foundation の主な機能を示します。  
  
|機能|説明|  
|--------|--------|  
|アクティビティのドラッグ アンド ドロップ|アクティビティを **\[ツールボックス\]** からデザイン サーフェイスまでドラッグすることにより、ワークフローを作成します。|  
|プロパティ ブラウザー|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の標準的な **\[プロパティ\]** ウィンドウを使用して、アクティビティのプロパティを構成します。|  
|ズーム|デザイン サーフェイス右側の垂直スクロール バーの下に、双眼鏡型の**ズーム レベル** アイコンがあります。ワークフローのグラフィック表示を拡大または縮小するには、双眼鏡をクリックしてズーム倍率を選択します。また、**パン** アイコン拡大鏡のカーソル オプションを使って拡大\/縮小することもできます。|  
|パン|**パン** アイコン \(4 方向を指す 4 つの交差矢印が描かれた円\) は、デザイン サーフェイス右側の垂直スクロール バーの下 \(双眼鏡ズーム アイコンのすぐ下\) にあります。パン アイコンをクリックすると、次のようなカーソル オプションがポップアップ メニューに表示されます。<br /><br /> -   **\[ズーム イン\]** 拡大鏡カーソルを使用すると、デザイン サーフェイスをクリックすることによってズーム インできます。<br />-   **\[ズーム アウト\]** 拡大鏡カーソルを使用すると、デザイン サーフェイスをクリックすることによってズーム アウトできます。<br />-   **\[ナビゲーション ツール\]** 手形カーソルを使用すると、デザイン サーフェイス内のワークフロー表示を"つかんで"、移動することができます。<br />-   **\[既定\]** 矢印カーソルを使用すると、他のカーソルから既定の矢印カーソルに戻すことができます。|  
|自動スクロール|ワークフローが大きいために、デザイン サーフェイスの表示領域外にアクティビティを配置する必要が生じる場合があります。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のデザイン サーフェイスでは、アクティビティを配置したい方向に最も近い側の端にアクティビティをドラッグすることができます。デザイン サーフェイスの表示が、その方向に自動的にスクロールされます。|  
|スマート タグ|構成が完了していないアクティビティ、または構成が有効でないアクティビティは、感嘆符アイコン付きで表示されます。このアイコンをクリックして表示されるドロップダウン リストで、アクティビティに存在する、必要な構成を確認できます。その後、**\[プロパティ\]** ウィンドウで、アクティビティを適切に構成することができます。アクティビティのすべてのプロパティが正しく構成されれば、感嘆符アイコンは表示されなくなります。|  
  
## このセクションの内容  
 [Visual Studio ワークフローのウィンドウ \(レガシ\)](../workflow-designer/visual-studio-workflow-windows-legacy.md)  
  
 [従来のワークフロー プロジェクトの作成](../workflow-designer/creating-legacy-workflow-projects.md)  
  
 [シーケンシャル ワークフロー ビュー \(レガシ\)](../workflow-designer/sequential-workflow-views-legacy.md)  
  
 [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)  
  
 [ワークフロー内でのテーマの使用 \(レガシ\)](../workflow-designer/using-themes-in-workflows-legacy.md)  
  
 [従来のステート マシン ワークフロー デザイナーの使用](../workflow-designer/using-the-legacy-state-machine-workflow-designer.md)  
  
 [従来のアクティビティ デザイナーの使用](../workflow-designer/using-the-legacy-activity-designer.md)  
  
 [従来の Designer for Windows Workflow Foundation UI ヘルプ](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)  
  
## 参照  
 [ワークフローの開発](http://go.microsoft.com/fwlink?LinkID=65010)