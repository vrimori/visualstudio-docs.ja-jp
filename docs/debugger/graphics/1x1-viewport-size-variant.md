---
title: 1 x 1 ビューポート サイズ バリアント |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3f645c078314522d767e578cc6d5770969971c5f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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