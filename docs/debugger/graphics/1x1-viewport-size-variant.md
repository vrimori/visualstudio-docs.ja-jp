---
title: "1 x 1 ビューポート サイズ バリアント |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 074cf7111108b7ae4f3b6866be19f0a12d3c429b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="1x1-viewport-size-variant"></a>1x1 ビューポイント サイズ バリアント
すべてのレンダー ターゲットでビューポートのディメンションを 1x1 ピクセルに減らします。  
  
## <a name="interpretation"></a>解釈  
 ビューポートを小さくすると、シェードが必要なピクセル数は減りますが、処理が必要な頂点の数は減りません。 ビューポートのディメンションを 1x1 ピクセルに設定すると、アプリケーションでピクセルのシェーディングを効果的に除去することができます。  
  
 このバリアントによりパフォーマンスが大幅に向上する場合は、アプリケーションで使用しているフィルレートが多すぎることを示しています。 これは、選択した解像度がターゲット プラットフォームに対して高すぎる、またはアプリケーションで、後に上書き (範囲を超えて描画) されるピクセルのシェーディングに多くの時間を消費していることを示している場合もあります。 この結果は、フレームバッファーのサイズを小さくすること、または範囲を超えて描画する領域を小さくすることによってアプリケーションのパフォーマンスが改善されることを意味しています。  
  
## <a name="remarks"></a>コメント  
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