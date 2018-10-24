---
title: ポイント、バイリニア、トリリニア、およびアニソトロ ピック テクスチャ フィルタ リング バリアント |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4958436e7b67872648c94c8aa65137a1297461c3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863114"
---
# <a name="point-bilinear-trilinear-and-anisotropic-texture-filtering-variants"></a>ポイント、バイリニア、トリリニア、およびアニソトロピック テクスチャ フィルタリング バリアント
適切なテクスチャのサンプラーでフィルタリング モードをオーバーライドします。  
  
## <a name="interpretation"></a>解釈  
 テクスチャ サンプリングにはさまざまなメソッドがありますが、それぞれパフォーマンス コストとイメージ品質が異なります。 次に、コストと表示品質の低い順からフィルター モードを示します。  
  
1. Point フィルタリング (最も安価、表示品質は一番低い)  
  
2. Bilinear フィルタリング  
  
3. Trilinear フィルタリング  
  
4. Anisotropic フィルタリング (最も高価、表示品質は一番高い)  
  
   各バリアントのパフォーマンス コストが重要である、またはより強力なフィルタリング モードを使用してパフォーマンス コストを強化する場合は、表示品質に対してコストに重点をおくことができます。 自身の評価に基づいて、パフォーマンス コストを追加して表示品質を向上させる、表示品質を落としてフレームレートの数を多くする、他の方法で使用できるようにパフォーマンスを改善する、といったことが可能です。  
  
   パフォーマンス コストがごくわずかであるか、またはフィルタリング モードに関係なく一定である (たとえば、ターゲットの GPU に大量のシェーダー スループットおよびメモリ帯域幅がある) 場合には、異方性フィルタリングを使用してアプリケーションで最高のイメージ品質を実現することを検討してください。  
  
## <a name="remarks"></a>Remarks  
 これらのバリアントは、アプリケーションが提供したサンプラーのフィルター モードが以下のいずれかの場合に、`ID3D11DeviceContext::PSSetSamplers` への呼び出しが行われたときにサンプラーの状態をオーバーライドします。  
  
- `D3D11_FILTER_MIN_MAG_MIP_POINT`  
  
- `D3D11_FILTER_MIN_MAG_POINT_MIP_LINEAR`  
  
- `D3D11_FILTER_MIN_POINT_MAG_LINEAR_MIP_POINT`  
  
- `D3D11_FILTER_MIN_POINT_MAG_MIP_LINEAR`  
  
- `D3D11_FILTER_MIN_LINEAR_MAG_MIP_POINT`  
  
- `D3D11_FILTER_MIN_LINEAR_MAG_POINT_MIP_LINEAR`  
  
- `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`  
  
- `D3D11_FILTER_MIN_MAG_MIP_LINEAR`  
  
- `D3D11_FILTER_ANISOTROPIC`  
  
  **Point Texture Filtering**バリアントで、アプリケーションが提供したフィルター モードが置き換えられます`D3D11_FILTER_MIN_MAG_MIP_POINT`; で、 **Bilinear Texture Filtering**バリアントでは置き換えられます`D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`;および、 **Trilinear Texture Filtering**バリアントでは置き換えられます`D3D11_FILTER_MIN_MAG_MIP_LINEAR`します。  
  
  **Anisotropic Texture Filtering**バリアントで、アプリケーションが提供したフィルター モードが置き換えられます`D3D11_FILTER_ANISOTROPIC`、Max Anisotropy は 16 に設定されているとします。  
  
## <a name="restrictions-and-limitations"></a>制約と制限  
 Direct3D では機能レベル 9.1 は、最大異方性が 2x であることを表します。 **Anisotropic Texture Filtering**バリアントは 16x を排他的に使用しようとしています、機能レベル 9.1 のデバイスでフレーム分析を実行するときに再生が失敗します。 この制約の影響を受ける現在のデバイスには、ARM ベースの Surface RT、および Surface 2 Windows タブレットが含まれています。 コンピューターの中には古い GPU が存在している可能性があり、これらの GPU も影響を受けます。ただし、これらは一般的には使われておらず、問題にならなくなっています。  
  
## <a name="example"></a>例  
 **Point Texture Filtering**このようなコードを使用してバリアントを再現することができます。  
  
```cpp
D3D11_SAMPLER_DESC sampler_description;  
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>例  
 **Bilinear Texture Filtering**このようなコードを使用してバリアントを再現することができます。  
  
```cpp
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>例  
 **Trilinear Texture Filtering**このようなコードを使用してバリアントを再現することができます。  
  
```cpp
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>例  
 **Anisotropic Texture Filtering**このようなコードを使用してバリアントを再現することができます。  
  
```cpp
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;  
sampler_description.MaxAnisotropy = 16;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```
