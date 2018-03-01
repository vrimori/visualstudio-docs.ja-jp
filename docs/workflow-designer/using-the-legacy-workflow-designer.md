---
title: "従来のワークフロー デザイナーの使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 7faec3b7a6bf33886928034e1f68ab31c7a60b03
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-legacy-workflow-designer"></a>従来のワークフロー デザイナーの使用
[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] が備えている従来の[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]を使用すると、[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象とすることができます。  
  
 どちらかを選択してアクセスした、 **.NET Framework 3.0**オプションまたは**.NET Framework 3.5**オプションで、ドロップダウン リストの上部にある、**新しいプロジェクト**ウィンドウです。 既定のオプションに[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]は**.NET Framework 4**作成に使用される[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]を対象とするアプリケーション、[!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)]です。  
  
 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] では、使い慣れた [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] ユーザー インターフェイスを使用して [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] アプリケーションをグラフィカルに作成できます。 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] アプリケーションは、アクティビティと呼ばれるワークフロー プロセス ステップで構成されます。 ワークフローを作成するには、デザイン サーフェイス上にアクティビティを作成、それぞれのアクティビティ デザイナーをドラッグすることで**ツールボックス**デザイン サーフェイスにします。  
  
 次の表に、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] for Windows Workflow Foundation の主な機能を示します。  
  
|機能|説明|  
|-------------|-----------------|  
|アクティビティのドラッグ アンド ドロップ|アクティビティをドラッグして、**ツールボックス**ワークフローを作成するデザイン サーフェイスにします。|  
|プロパティ ブラウザー|標準**プロパティ**ウィンドウ[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]アクティビティのプロパティを構成するために使用します。|  
|ズーム|双眼鏡**拡大レベル**アイコンは、デザイン画面の右側にある垂直スクロール バーの下に配置します。 ワークフローのグラフィック表示を拡大または縮小するには、双眼鏡をクリックしてズーム倍率を選択します。使用することも、**パン**拡大および縮小するアイコン拡大鏡のカーソル オプションです。|  
|パン|**パン**アイコン、4 つの方向を指す 4 つの交差矢印を含んだ円ですが、双眼鏡ズーム アイコンのすぐ下、デザイン画面の右側にある垂直スクロール バーの下にあります。 パン アイコンをクリックすると、次のようなカーソル オプションがポップアップ メニューに表示されます。<br /><br /> -**ズームイン**拡大鏡カーソルを使用して、デザイン サーフェイスをクリックしてズーム インできます。<br />-**ズーム アウト**拡大鏡カーソルでは、デザイン サーフェイスをクリックしてズーム アウトすることができます。<br />-**ナビゲーション ツール**手形カーソルでは、「つかんで」、ワークフロー デザイン サーフェイスでのビューを移動することができます。<br />-**既定**矢印カーソルを使用して、他のカーソルから既定の矢印カーソルに切り替えることができます。|  
|自動スクロール|ワークフローが大きいために、デザイン サーフェイスの表示領域外にアクティビティを配置する必要が生じる場合があります。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のデザイン サーフェスでは、アクティビティを配置したい方向に最も近い側の端にアクティビティをドラッグすることができます。 デザイン サーフェイスの表示が、その方向に自動的にスクロールされます。|  
|スマート タグ|構成が完了していないアクティビティ、または構成が有効でないアクティビティは、感嘆符アイコン付きで表示されます。 このアイコンをクリックして表示されるドロップダウン リストで、アクティビティに存在する、必要な構成を確認できます。 使用してできます、**プロパティ**ウィンドウ、アクティビティを適切に構成します。 アクティビティのすべてのプロパティが正しく構成されれば、感嘆符アイコンは表示されなくなります。|  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Visual Studio ワークフローのウィンドウ (レガシ)](../workflow-designer/visual-studio-workflow-windows-legacy.md)  
  
 [従来のワークフロー プロジェクトの作成](../workflow-designer/creating-legacy-workflow-projects.md)  
  
 [シーケンシャル ワークフロー ビュー (レガシ)](../workflow-designer/sequential-workflow-views-legacy.md)  
  
 [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)  
  
 [ワークフロー内でのテーマの使用 (レガシ)](../workflow-designer/using-themes-in-workflows-legacy.md)  
  
 [従来のステート マシン ワークフロー デザイナーの使用](../workflow-designer/using-the-legacy-state-machine-workflow-designer.md)  
  
 [従来のアクティビティ デザイナーの使用](../workflow-designer/using-the-legacy-activity-designer.md)  
  
 [従来の Designer for Windows Workflow Foundation UI ヘルプ](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)  
  
## <a name="see-also"></a>参照  
 [ワークフローの開発](http://go.microsoft.com/fwlink?LinkID=65010)