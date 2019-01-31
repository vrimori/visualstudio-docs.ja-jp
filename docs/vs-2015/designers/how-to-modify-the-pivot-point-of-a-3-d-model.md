---
title: '方法: 3-D モデルのピボット ポイントの変更 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7b28a279e729900d8a1cb26f25bca6370c00a08c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54774102"
---
# <a name="how-to-modify-the-pivot-point-of-a-3-d-model"></a>方法: 3-D モデルのピボット ポイントを変更します。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このドキュメントでは、モデル エディターを使用した 3-D モデルの*ピボット ポイント*の変更方法を示します。 ピボット ポイントは、オブジェクトの回転と拡大縮小の数学的な中心を定義する空間内のポイントです。  
  
 このドキュメントでは、以下のアクティビティについて説明します:  
  
-   オブジェクトのピボット ポイントの変更  
  
## <a name="modifying-the-pivot-point-of-a-3-d-model"></a>3-D モデルのピボット ポイントの変更  
 ピボット ポイントを変更することにより、3-D モデルの原点を再定義できます。  
  
 **[プロパティ]** ウィンドウと **[ツールボックス]** が表示されていることを確認します。  
  
#### <a name="to-modify-the-pivot-point-of-a-3-d-model"></a>3-D モデルのピボット ポイントを変更するには  
  
1. 説明されているものなどの既存の 3-D モデルから始めます[方法。基本的な 3-D モデルを作成](../designers/how-to-create-a-basic-3-d-model.md)です。  
  
2. ピボット モードを開始します。 **[モデル エディターのモード]** ツール バーで、**[ピボット モード]** をクリックしてピボット モードをアクティブにします。 **[ピボット モード]** を囲むボックスが表示されて、モデル エディターがピボット モードになっていることが示されます。 ピボット モードでは、平行移動などの操作は、ワールド空間内のオブジェクトの構造ではなくオブジェクトのピボット ポイントに影響を与えます。  
  
3. オブジェクトのピボット ポイントを変更します。 **[選択]** モードでオブジェクトを選択してから、**[モデル ビューアー]** のツール バーで **[平行移動]** ツールを選択します。 ピボット ポイントを表すボックスがデザイン サーフェイスに表示されます。 ボックスを移動してオブジェクトのピボット ポイントを変更します。  
  
    ボックスを移動することによって、3 つすべての次元方向にピボット ポイントを移動できます。 1 つの軸に沿ってピボット ポイントを移動するには、その軸に対応する矢印を移動します。 ボックスと矢印が黄色に変わり、移動によって影響を受ける軸が示されます。  
  
    **[プロパティ]** ウィンドウで **[ピボット平行移動]** プロパティを使用して、ピボット ポイントを移動することもできます。  
  
   > [!TIP]
   >  オブジェクトを回転することで新しいピボット ポイントの効果を表示できます。 回転するには、**[回転]** ツールを使用するか、**[回転]** プロパティを変更します。  
  
   変更されたピボット ポイントを含むモデルを次に示します。  
  
   ![変更されたピボット ポイントを含む家のモデル](../designers/media/digit-modified-model.png "Digit-Modified-Model")  
  
## <a name="see-also"></a>「  
 [方法: 基本的な 3-D モデルを作成します。](../designers/how-to-create-a-basic-3-d-model.md)   
 [モデル エディター](../designers/model-editor.md)
