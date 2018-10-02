---
title: 1 x 1 ビューポート サイズ バリアント |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c0052a2d59dbcef1d7ea32eab789ab955750f3f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47549067"
---
# <a name="1x1-viewport-size-variant"></a>1x1 ビューポイント サイズ バリアント
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[1 x 1 ビューポート サイズ バリアント](https://docs.microsoft.com/visualstudio/debugger/graphics/1x1-viewport-size-variant)します。  
  
すべてのレンダー ターゲットでビューポートのディメンションを 1x1 ピクセルに減らします。  
  
## <a name="interpretation"></a>解釈  
 ビューポートを小さくすると、シェードが必要なピクセル数は減りますが、処理が必要な頂点の数は減りません。 ビューポートのディメンションを 1x1 ピクセルに設定すると、アプリケーションでピクセルのシェーディングを効果的に除去することができます。  
  
 このバリアントによりパフォーマンスが大幅に向上する場合は、アプリケーションで使用しているフィルレートが多すぎることを示しています。 これは、選択した解像度がターゲット プラットフォームに対して高すぎる、またはアプリケーションで、後に上書き (範囲を超えて描画) されるピクセルのシェーディングに多くの時間を消費していることを示している場合もあります。 この結果は、フレームバッファーのサイズを小さくすること、または範囲を超えて描画する領域を小さくすることによってアプリケーションのパフォーマンスが改善されることを意味しています。  
  
## <a name="remarks"></a>Remarks  
 `ID3D11DeviceContext::OMSetRenderTargets` または `ID3D11DeviceContext::RSSetViewports` への呼び出しが行われるたびに、ビューポートのディメンションは 1x1 ピクセルにリセットされます。  
  
## <a name="example"></a>例  
 このバリアントは次のようなコードを使用して再現することができます。  
  
```  
D3D11_VIEWPORT viewport;  
viewport.TopLeftX = 0;  
viewport.TopLeftY = 0;  
viewport.Width = 1;  
viewport.Height = 1;  
d3d_context->RSSetViewports(1, &viewport);  
```



