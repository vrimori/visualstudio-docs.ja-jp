---
title: ポイント、バイリニア、トリリニア、およびアニソトロ ピック テクスチャ フィルタ リング バリアント |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89ea960e703603f76177050695fe6c12eabaf4e0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540291"
---
# <a name="point-bilinear-trilinear-and-anisotropic-texture-filtering-variants"></a>ポイント、バイリニア、トリリニア、およびアニソトロピック テクスチャ フィルタリング バリアント
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ポイント、バイリニア、トリリニア、およびアニソトロ ピック テクスチャ フィルタ リング バリアント](https://docs.microsoft.com/visualstudio/debugger/graphics/point-bilinear-trilinear-and-anisotropic-texture-filtering-variants)します。  
  
適切なテクスチャのサンプラーでフィルタリング モードをオーバーライドします。  
  
## <a name="interpretation"></a>解釈  
 テクスチャ サンプリングにはさまざまなメソッドがありますが、それぞれパフォーマンス コストとイメージ品質が異なります。 次に、コストと表示品質の低い順からフィルター モードを示します。  
  
1.  Point フィルタリング (最も安価、表示品質は一番低い)  
  
2.  Bilinear フィルタリング  
  
3.  Trilinear フィルタリング  
  
4.  Anisotropic フィルタリング (最も高価、表示品質は一番高い)  
  
 各バリアントのパフォーマンス コストが重要である、またはより強力なフィルタリング モードを使用してパフォーマンス コストを強化する場合は、表示品質に対してコストに重点をおくことができます。 自身の評価に基づいて、パフォーマンス コストを追加して表示品質を向上させる、表示品質を落としてフレームレートの数を多くする、他の方法で使用できるようにパフォーマンスを改善する、といったことが可能です。  
  
 パフォーマンス コストがごくわずかであるか、またはフィルタリング モードに関係なく一定である (たとえば、ターゲットの GPU に大量のシェーダー スループットおよびメモリ帯域幅がある) 場合には、異方性フィルタリングを使用してアプリケーションで最高のイメージ品質を実現することを検討してください。  
  
## <a name="remarks"></a>Remarks  
 これらのバリアントは、アプリケーションが提供したサンプラーのフィルター モードが以下のいずれかの場合に、`ID3D11DeviceContext::PSSetSamplers` への呼び出しが行われたときにサンプラーの状態をオーバーライドします。  
  
-   `D3D11_FILTER_MIN_MAG_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_MAG_POINT_MIP_LINEAR`  
  
-   `D3D11_FILTER_MIN_POINT_MAG_LINEAR_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_POINT_MAG_MIP_LINEAR`  
  
-   `D3D11_FILTER_MIN_LINEAR_MAG_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_LINEAR_MAG_POINT_MIP_LINEAR`  
  
-   `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_MAG_MIP_LINEAR`  
  
-   `D3D11_FILTER_ANISOTROPIC`  
  
 **Point Texture Filtering**バリアントで、アプリケーションが提供したフィルター モードが置き換えられます`D3D11_FILTER_MIN_MAG_MIP_POINT`; で、 **Bilinear Texture Filtering**バリアントでは置き換えられます`D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`;および、 **Trilinear Texture Filtering**バリアントでは置き換えられます`D3D11_FILTER_MIN_MAG_MIP_LINEAR`します。  
  
 **Anisotropic Texture Filtering**バリアントで、アプリケーションが提供したフィルター モードが置き換えられます`D3D11_FILTER_ANISOTROPIC`、Max Anisotropy は 16 に設定されているとします。  
  
## <a name="restrictions-and-limitations"></a>制約と制限  
 Direct3D では機能レベル 9.1 は、最大異方性が 2x であることを表します。 **Anisotropic Texture Filtering**バリアントは 16x を排他的に使用しようとしています、機能レベル 9.1 のデバイスでフレーム分析を実行するときに再生が失敗します。 この制約の影響を受ける現在のデバイスには、ARM ベースの Surface RT、および Surface 2 Windows タブレットが含まれています。 コンピューターの中には古い GPU が存在している可能性があり、これらの GPU も影響を受けます。ただし、これらは一般的には使われておらず、問題にならなくなっています。  
  
## <a name="example"></a>例  
 **Point Texture Filtering**このようなコードを使用してバリアントを再現することができます。  
  
```  
D3D11_SAMPLER_DESC sampler_description;  
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>例  
 **Bilinear Texture Filtering**このようなコードを使用してバリアントを再現することができます。  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>例  
 **Trilinear Texture Filtering**このようなコードを使用してバリアントを再現することができます。  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>例  
 **Anisotropic Texture Filtering**このようなコードを使用してバリアントを再現することができます。  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;  
sampler_description.MaxAnisotropy = 16;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```



