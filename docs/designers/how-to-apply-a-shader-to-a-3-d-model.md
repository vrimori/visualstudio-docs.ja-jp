---
title: "方法: シェーダーを 3-D モデルに適用する | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 852baa1c8a2b627e5426411d8c156ab28d5c6614
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-a-shader-to-a-3-d-model"></a>方法: シェーダーを 3-D モデルに適用する
このドキュメントでは、モデル エディターを使用して、Directed Graph Shader Language (DGSL) シェーダーを 3-D モデルに適用する方法を説明します。  
  
 このドキュメントでは、以下のアクティビティについて説明します。  
  
-   シェーダーを 3-D モデルに適用する  
  
## <a name="applying-a-shader-to-a-3-d-model"></a>シェーダーを 3-D モデルに適用する  
 シェーダー効果を 3-D モデルに適用して、魅力的な外観にすることができます。  
  
 開始する前に、**[プロパティ]** ウィンドウが表示されていることを確認します。  
  
#### <a name="to-apply-a-shader-to-a-3-d-model"></a>シェーダーを 3-D モデルに適用する方法  
  
1.  まず 1 つ以上のモデルを含む 3-D シーンを使用します。 適切な 3-D シーンがない場合、「[方法: 基本 3-D モデルを作成する](../designers/how-to-create-a-basic-3-d-model.md)」に従って作成します。 また、モデルに適用できる DGSL シェーダーを使用する必要があります。 適切なシェーダーがない場合、「[方法: 基本カラー シェーダーを作成する](../designers/how-to-create-a-basic-color-shader.md)」に従って作成し、ファイルに保存してから続行してください。  
  
2.  **選択**モードで、シェーダーを適用するモデルを選択します。その後、**[プロパティ]** ウィンドウを開き、**効果**プロパティ グループの **Filename** プロパティで、モデルに適用する DGSL シェーダーを指定します。  
  
 基本色の効果を適用したモデルはこちらです。  
  
 ![基本色の効果を表示する 3&#45;D シーン](../designers/media/digit-3d-model-effect.png "Digit-3D-Model-Effect")  
  
 シェーダーをモデルに適用した後、それをシェーダー デザイナーで開くには、モデルを選択します。その後、**[プロパティ]** ウィンドウを開き、**効果** プロパティ グループの**(詳細設定)** プロパティで省略記号 (**...**) ボタンを選択します。  
  
## <a name="see-also"></a>参照  
 [方法: 基本 3-D モデルを作成する](../designers/how-to-create-a-basic-3-d-model.md)   
 [方法: 基本カラー シェーダーを作成する](../designers/how-to-create-a-basic-color-shader.md)   
 [モデル エディター](../designers/model-editor.md)   
 [シェーダー デザイナー](../designers/shader-designer.md)