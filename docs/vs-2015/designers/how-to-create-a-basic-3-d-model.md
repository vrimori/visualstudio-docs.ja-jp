---
title: '方法: 基本的な 3-D モデルの作成 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c7c904e74793710dedc96d4a769d4f6c61a15e69
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54760772"
---
# <a name="how-to-create-a-basic-3-d-model"></a>方法: 基本的な 3-D モデルを作成します。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このドキュメントでは、モデル エディターを使用した基本 3-D モデルの作成方法を示します。  
  
 このドキュメントでは、以下のアクティビティについて説明します。  
  
-   シーンへのオブジェクトの追加  
  
-   面とエッジの選択  
  
-   選択範囲の変換  
  
-   **[面を再分割する]** および **[面を浮き出し表示にする]** ツールの使用  
  
-   **[三角形に変換]** コマンドの使用  
  
## <a name="creating-a-basic-3-d-model"></a>基本 3-D モデルの作成   
 モデル エディターを使用すると、ゲームやアプリの 3-D モデルやシーンを作成したり変更したりできます。 次の手順では、モデル エディターを使用して、家の簡易 3-D モデルを作成する方法を示します。 簡易モデルは、まだ作成中の最終的なアート アセットの代わりとして、または衝突検出用のメッシュとして使用できます。あるいは、表現するオブジェクトを詳細にレンダリングしてもほとんど役に立たない場合に、詳細度の低いモデルとして使用することもできます。  
  
 完成したモデルの様子を示します。  
  
 ![簡単な家の完成したモデル](../designers/media/gfx-model-demo-house-final.png "gfx_model_demo_house_final")  
  
 開始する前に、**[プロパティ]** ウィンドウと**ツールボックス**が表示されていることを確認します。  
  
#### <a name="to-create-a-simplified-3-d-model-of-a-house"></a>家の簡易 3-D モデルを作成するには  
  
1. 処理する 3-D モデルを作成します。 プロジェクトにモデルを追加する方法に関する詳細については、「[モデル エディター](../designers/model-editor.md)」の「作業の開始」セクションを参照してください。  
  
2. 直方体をシーンに追加します。 **[ツールボックス]** ウィンドウの **[図形]** で **[直方体]** を選択し、デザイン サーフェイスに移動します。  
  
3. 面選択に切り替えます。 [モデル エディター] ツール バーで、**[面の選択]** を選択します。  
  
4. 直方体の上部を再分割します。 面選択モードで、直方体を 1 回クリックして、選択できるようにアクティブにしてから、直方体の上部をクリックして、上部の面を選択します。 [モデル エディター] ツール バーで、**[面を再分割する]** を選択します。 直方体の上部を均等なサイズの 4 つのパーティションに分割する新しい頂点が追加されます。  
  
    ![直方体の上部が再分割されました](../designers/media/gfx-model-demo-house-subdiv.png "gfx_model_demo_house_subdiv")  
  
5. 直方体の隣接した 2 つの面を浮き出し表示にします。たとえば、直方体の前面と右面です。 面選択モードで、直方体を 1 回クリックして、選択できるようにアクティブにしてから、直方体の 1 つの面を選択します。 Ctrl キーを長押しして、最初に選択した面に隣接した別の面を直方体から選択し、[モデル エディター] ツール バーで、**[面を浮き出し表示にする]** を選択します。  
  
    ![直方体の面が押し出されました](../designers/media/gfx-model-demo-house-extrude.png "gfx_model_demo_house_extrude")  
  
6. 一方の浮き出しを拡大します。 浮き出し表示したばかりの面の 1 つを選択し、[モデル エディター] ツール バーで、**[変換]** ツールを選択して、変換マニピュレーターを浮き出しと同じ方向に移動します。  
  
    ![直方体の一面がさらに押し出されました。](../designers/media/gfx-model-demo-house-extend.png "gfx_model_demo_house_extend")  
  
7. モデルを三角形に変換します。 [モデル エディター] ツール バーで、**[詳細]**、**[ツール]**、**[三角形に変換]** の順に選択します。  
  
8. 家の屋根を作成します。 [モデル エディター] ツール バーで、**[エッジの選択]** を選択してエッジ選択モードに切り替え、直方体を選択してアクティブにします。 Ctrl キーを長押しして、ここに表示されるエッジ群を選択します。  
  
    ![屋根の頂点を形成するエッジ](../designers/media/gfx-model-demo-house-edges.png "gfx_model_demo_house_edges")  
  
    エッジが選択できたら、[モデル エディター] ツール バーで **[変換]** ツールを選択し、変換マニピュレーターを上方に移動して家の屋根を作成します。  
  
   簡単な家のモデルが完成しました。 フラット シェーディングを適用した最終的なモデルを次にもう一度示します。  
  
   ![簡単な家の完成したモデル](../designers/media/gfx-model-demo-house-final.png "gfx_model_demo_house_final")  
  
   次の手順として、この 3-D モデルにシェーダーを適用できます。 詳細については、「[方法:シェーダーを 3-D モデルに適用する](../designers/how-to-apply-a-shader-to-a-3-d-model.md)します。  
  
## <a name="see-also"></a>「  
 [方法: 3-D 地形をモデル](../designers/how-to-model-3-d-terrain.md)   
 [モデル エディター](../designers/model-editor.md)   
 [シェーダー デザイナー](../designers/shader-designer.md)
