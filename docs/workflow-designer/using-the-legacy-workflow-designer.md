---
title: 従来のワークフロー デザイナーの使用 |Microsoft ドキュメント
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 700434451d8390b9875a290b428c2173953cbb8f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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

## <a name="see-also"></a>関連項目

- [ワークフローの開発](http://go.microsoft.com/fwlink?LinkID=65010)