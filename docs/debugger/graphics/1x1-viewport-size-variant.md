---
title: 1 x 1 ビューポート サイズ バリアント |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 168b358bf58dcb2c91814f5460b203873255e275
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433247"
---
# <a name="1x1-viewport-size-variant"></a>1x1 ビューポイント サイズ バリアント
すべてのレンダー ターゲットでビューポートのディメンションを 1x1 ピクセルに減らします。  
  
## <a name="interpretation"></a>解釈  
 ビューポートを小さくでは、網掛けする必要があるピクセルの数を減らします。 ビューポートを小さくする必要がある頂点の数を削減しませんが、処理します。 ビューポートのディメンションを 1x1 ピクセルに設定すると、アプリケーションでピクセルのシェーディングを効果的に除去することができます。  
  
 このバリアントでは、大規模なパフォーマンスの向上を示している場合、アプリが多すぎるのフィル レートを使用していることを示す場合します。 さらの解像度は、ターゲット プラットフォームに対して高すぎる可能性がありますか、アプリは、後で上書きされるピクセルの膨大な時間シェーディングを費やすことができました、別名*オーバー ドロー*します。 小さなフレーム バッファーまたはアルファブレンディングを減らすには、アプリのパフォーマンスが向上します。  
  
## <a name="remarks"></a>Remarks  
 `ID3D11DeviceContext::OMSetRenderTargets` または `ID3D11DeviceContext::RSSetViewports` への呼び出しが行われるたびに、ビューポートのディメンションは 1x1 ピクセルにリセットされます。  
  
## <a name="example"></a>例  
 このバリアントは、次のコードで再現ことができます。  
  
```cpp
D3D11_VIEWPORT viewport;  
viewport.TopLeftX = 0;  
viewport.TopLeftY = 0;  
viewport.Width = 1;  
viewport.Height = 1;  
d3d_context->RSSetViewports(1, &viewport);  
```
