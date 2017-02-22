---
title: "方法: シェーダーを 3-D モデルに適用する | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
caps.latest.revision: 15
caps.handback.revision: 15
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# 方法: シェーダーを 3-D モデルに適用する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このドキュメントでは、3\-D モデルに Directed Graph Shader Language \(DGSL\) シェーダーを適用するには、モデル エディターを使用する方法を示します。  
  
 このドキュメントでは、このアクティビティについて説明します。  
  
-   3\-D モデルへのシェーダーの適用  
  
## 3\-D モデルへのシェーダーの適用  
 3\-D モデルにシェーダー エフェクトを適用すると、3\-D モデルに魅力的な外観を持たせることができます。  
  
 開始する前に、**\[プロパティ\]** ウィンドウが表示されていることを確認します。  
  
#### 3\-D モデルにシェーダーを適用するには  
  
1.  一つ以上のモデルを含む 3\-D シーンから開始します。  適切な 3\-D シーンがない場合は、[方法: 基本 3\-D モデルを作成する](../Topic/How%20to:%20Create%20a%20Basic%203-D%20Model.md)"に説明されているように、1 種類を作成します。  また、モデルに適用できる DGSL シェーダーが必要です。  適切なシェーダーがない場合は、1 を [方法: 基本カラー シェーダーを作成する](../designers/how-to-create-a-basic-color-shader.md) "に説明されているように作成し、次の手順に進む前にファイルに保存されていることを確認します。  
  
2.  **\[選択\]** モードで、次にシェーダーを適用する **\[プロパティ\]** ウィンドウで、**\[効果\]** プロパティ グループの **\[Filename\]** のプロパティでモデルに適用する DGSL シェーダーを指定します。モデルを選択します。  
  
 適用される基本色の影響を及ぼすモデルがあります:  
  
 ![基本色の効果を表示する 3D シーン](../designers/media/digit-3d-model-effect.png "Digit\-3D\-Model\-Effect")  
  
 モデルにシェーダーを適用すると、モデルと**...**します。次に、省略記号 \(\) ボタンをクリックします **\[効果\]** プロパティ グループの **\[\(詳細\)\]** のプロパティの **\[プロパティ\]** ウィンドウでコマンドを選択して、シェーダー デザイナー、開くことができます。  
  
## 参照  
 [方法: 基本 3\-D モデルを作成する](../Topic/How%20to:%20Create%20a%20Basic%203-D%20Model.md)   
 [方法: 基本カラー シェーダーを作成する](../designers/how-to-create-a-basic-color-shader.md)   
 [モデル エディター](../designers/model-editor.md)   
 [シェーダー デザイナー](../designers/shader-designer.md)