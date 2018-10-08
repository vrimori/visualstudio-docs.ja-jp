---
title: '方法: 基本カラー シェーダーを作成する | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 23a7082c305bdabf139e284d448fafdf375762e2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536938"
---
# <a name="how-to-create-a-basic-color-shader"></a>方法: 基本カラー シェーダーを作成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: 基本カラー シェーダーを作成する](https://docs.microsoft.com/visualstudio/designers/how-to-create-a-basic-color-shader)します。  
  
このドキュメントでは、シェーダー デザイナーと DGSL (Directed Graph Shader Language) を使用して単色シェーダーを作成する方法を示します。 このシェーダーは、最終的な色を定数の RGB カラー値に設定します。  
  
 このドキュメントでは、以下のアクティビティについて説明します。  
  
-   グラフからのノードの削除  
  
-   グラフへのノードの追加  
  
-   ノードのプロパティの設定  
  
-   ノードの接続  
  
## <a name="creating-a-flat-color-shader"></a>単色シェーダーの作成  
 RGB 色定数のカラー値を最終的な出力の色に書き込めば、単色シェーダーを実装できます。  
  
 開始する前に、**[プロパティ]** ウィンドウと**ツールボックス**が表示されていることを確認します。  
  
#### <a name="to-create-a-flat-color-shader"></a>単色シェーダーを作成するには  
  
1.  操作する DGSL シェーダーを作成します。 プロジェクトに DGSL シェーダーを追加する方法に関する詳細については、「[シェーダー デザイナー](../designers/shader-designer.md)」の「作業の開始」セクションを参照してください。  
  
2.  **[ポイントの色]** ノードを削除します。 **[選択]** ツールを使用して、**[ポイントの色]** ノードを選択し、メニュー バーで **[編集]**、**[削除]** を選択します。  
  
3.  **[色定数]** ノードをグラフに追加します。 **ツールボックス**の **[定数]** で **[色定数]** を選択し、デザイン サーフェイスに移動します。  
  
4.  **[色定数]** ノードのカラー値を指定します。 **[選択]** ツールを使用して、**[色定数]** ノードを選択し、**[プロパティ]** ウィンドウの **[出力]** プロパティで、カラー値を指定します。 オレンジの場合は、値 (1.0, 0.5, 0.2, 1.0) を指定します。  
  
5.  色定数を最終的な色に接続します。 接続を作成するには、**[色定数]** ノードの **[RGB]** ターミナルを **[最終的な色]** ノードの **[RGB]** ターミナルに移動してから、**[色定数]** ノードの **[アルファ]** ターミナルを **[最終的な色]** ノードの **[アルファ]** ターミナルに移動します。 これらの接続によって、最終的な色が、前の手順で定義された色定数に設定されます。  
  
 次の図は、完成したシェーダー グラフと、直方体に適用されるシェーダーのプレビューを示します。  
  
> [!NOTE]
>  この図では、シェーダーの効果をわかりやすく示すために、オレンジ色が指定されました。  
  
 ![3&#45;D モデルのシェーダー グラフとその結果](../designers/media/digit-flat-color-effect.png "Digit-Flat-Color-Effect")  
  
 シェーダーによっては、特定の図形を使用すると、より適切にプレビューできる可能性があります。 シェーダー デザイナーでシェーダーをプレビューする方法に関する詳細については、「[シェーダー デザイナー](../designers/shader-designer.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [方法: シェーダーを 3-D モデルに適用する](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [方法: シェーダーをエクスポートする](../designers/how-to-export-a-shader.md)   
 [シェーダー デザイナー](../designers/shader-designer.md)   
 [シェーダー デザイナー ノード](../designers/shader-designer-nodes.md)



