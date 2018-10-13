---
title: 1 x 1 ビューポート サイズ バリアント |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: ea21a12cb8bf1b37524a4b563c70a43eeed6f7f2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49184874"
---
# <a name="1x1-viewport-size-variant"></a>1x1 ビューポイント サイズ バリアント
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



