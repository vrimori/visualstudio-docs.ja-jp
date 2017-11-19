---
title: "ワークフロー デザイナーのシェルの機能 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: c2c3083daec31620efa9f9665443d9d35b06804b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="workflow-designer-shell-features"></a>ワークフロー デザイナーのシェルの機能
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]は、デザイナー画面、その上の階層リンク バー、およびその下のシェルという 3 つの主要な UI 領域で構成されています。 階層リンク バーは画面の上部に位置し、現在のルート アクティビティの先祖の一覧を表示するために使用されます。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][方法: 階層リンク バー ナビゲーションを使用して](../workflow-designer/how-to-use-breadcrumb-navigation.md)です。 デザイナー画面は画面の中央に位置し、ワークフローを作成するために使用されます。 シェルは画面の下部に位置しており、ここには、現在のビューを管理するためのさまざまなボタンが含まれています。  
  
## <a name="shell-features"></a>シェルの機能  
 シェルのバーの右側にあるボタンを使用して、ワークフローのズームインとズームアウト、画面のサイズに合わせたワークフローの内容の調整、および概要マップの表示/非表示の切り替えを行うことができます。 ワークフローのズームインとズームアウトは、キーボード ショートカットでも実行できます。Ctrl キーを押しながら、+ キーを押すとズームインし、- キーを押すとズームアウトします。  
  
## <a name="overview-map"></a>概要マップ  
 概要マップには、現在の階層リンク ルートでのアクティビティ全体が縮小表示されます。これには、すべての子、およびその展開された子のすべてが含まれます。 オレンジ色の罫線に囲まれた四角形のビューポートによって、エディター内で現在表示されているアクティビティの一部が示されます。 この四角形を概要マップ内でドラッグすると、ワークフロー デザイナーがスクロールされ、エディターのビューが変化します。  
  
> [!NOTE]
>  [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] ユーザー インターフェイスは仮想化されています。 アクティビティ デザイナーは、必要なときにのみ表示されます。 デザイナー画面でワークフローの一部がまだ描画されていない場合は、その部分が概要マップで白く表示されます。 概要マップをスクロールすると、ワークフロー全体が描画されます。  
  
## <a name="copying-or-saving-workflows-as-images"></a>ワークフローをイメージとしてコピーまたは保存  
 ワークフローは、ビットマップ形式でのコピーや、ビットマップまたはベクター形式での保存が可能です。 イメージをコピーまたは保存すると、現在の階層リンク ルートにおけるアクティビティ全体 (すべての子およびそれらの展開された子のすべてを含む) のビューを別のプログラムにエクスポートできます。  
  
 イメージとしてコピーするに右クリックし、デザイナーで**イメージとしてコピー**です。 をイメージとして保存する内を右クリック、デザイナーと選択**イメージとして保存**です。 ワークフローは、JPG、PNG、GIF、および XPS の各形式のいずれかで保存できます。 形式を選択、**名前を付けて保存** ダイアログ ボックスで、**ファイルの種類:**  ウィンドウの下部にあるボックスの一覧です。  
  
## <a name="fonts-and-colors"></a>フォントと色  
 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 内の[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]で使用する色は、環境フォントにより制御されます。 オペレーティング システムのテーマにハイコントラストの配色を使用している場合は、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]で表示される色が変わります。 フォントまたは色の設定の変更後に[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]で変更を有効にするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] を再起動する必要があります。