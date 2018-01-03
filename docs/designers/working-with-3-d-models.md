---
title: "3-D モデルの操作 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa035091-1354-4d1c-be44-4fb83860466f
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 372a1efccbfa211167930710418905d95411760c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-3-d-models"></a>3-D モデルの操作
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でモデル エディターを使って 3-D モデルを作成できます。 作成したモデルは、DirectX ベースのゲームやアプリで使うことができます。  
  
## <a name="3-d-models"></a>3-D モデル  
 3-D モデルでは、3-D シーン内に存在するオブジェクトのシェイプが定義されています。 基本的な単独のオブジェクト、基本オブジェクトの階層から形成される複雑なオブジェクト、さらには 3-D シーン全体のモデルさえ作成できます。 3-D オブジェクトは、3-D 空間内のポイント ("*頂点*" と呼ばれます)、これらのポイントから作られる三角形、線、他のプリミティブを定義するインデックス、および頂点単位またはプリミティブ単位に適用される属性 (サーフェスの法線など) で構成されます。 さらに、一部の情報はオブジェクトごとに適用されることがあります (例: オブジェクトに固有の外観を与えるシェーダーやテクスチャ)。  
  
 ゲームまたはアプリで使うことができる、素材のプロパティ、テクスチャ、ピクセル シェーダーを備えた基本的な 3-D モデルを作成するために必要なツールは、モデル エディターだけです。 または、アーティストにモデルのしあげを任せる前に、プレースホルダー モデルを作成してプロトタイプやテストを行うことができます。  
  
 モデル エディターを使うと、全機能を備えたツールを使って作成された既存の 3-D モデルを表示し、アート資産で問題が見つかった場合は修正することもできます。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[モデル エディター](../designers/model-editor.md)|モデル エディターを使って 3-D モデルを操作する方法について説明します。|  
|[モデル エディターの例](../designers/model-editor-examples.md)|モデル エディターを使って一般的な 3-D モデリング タスクを実行する方法がわかるトピックへのリンクが提供されています。|