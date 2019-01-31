---
title: 図形とパスの描画
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31673371e1feae9c31c6041a076fde939175e6b1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54998340"
---
# <a name="draw-shapes-and-paths"></a>図形とパスの描画

XAML デザイナーでは、"*図形*" とはその名の示すとおりのものです。 たとえば、四角形、円、楕円などです。 *パス* は、より柔軟なバージョンの図形です。 図形の形状を変更したり、図形を結合して新しい図形を形成するといった操作ができます。

図形とパスではベクター グラフィックスを使用するため、高解像度表示に対応して拡大縮小できます。 ベクター グラフィックスの詳細については、 [ベクター グラフィックスに関するビデオ](https://www.youtube.com/watch?v=MoCSwF0n-io) や [ベクター グラフィックスに関するページ](http://www.webopedia.com/TERM/V/vector_graphics.html)を参照してください。

##  <a name="Shape"></a> 図形の描画
 図形は **[アセット]** パネルにあります。

 ![[アセット] パネルの [図形] カテゴリ](../designers/media/b4_shapes_assetspanel.png)

 目的の図形をアートボードにドラッグします。 次に、図形にあるハンドルを使用して、図形の拡大縮小、回転、移動、または傾斜を行います。

 ![Handles](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png)

##  <a name="Path"></a> パスの描画
 パスは、直線と曲線が連結して一続きになったものです。 パスを使用すると、 **[アセット]** パネルでは使用できない面白い図形を作成できます。

 パスの描画には直線、ペン、または鉛筆を使用します。 これらのツールは **[ツール]** パネルにあります。

 ![[ペン] ツール](../designers/media/717956a8-b6a5-4e37-8af3-70bcfc78c82a.png) ![[ペン] ツールのオプション](../designers/media/8fbbbb21-be83-4cf6-903b-3a49f00c9860.png)

### <a name="draw-a-straight-line"></a>直線の描画
 **[ペン]** ツール ![ペン ツール](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png) または **[直線]** ツール ![直線ツール](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png) を使用します。

 **ペン ツールの使用** ![ペン ツール](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png)

 アートボード上で 1 回クリックし、始点を定義します。次に、再度クリックして直線の終わりを定義します。

 **ペン ツールの使用** ![直線ツール](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png)

 アートボード上で、直線の始点からドラッグして、終点でマウス ボタンを放します。

### <a name="draw-a-curve"></a>曲線の描画
 **[ペン]** ツール ![ペン ツール](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png) を使用します。

 アートボード上で 1 回クリックして、直線の始点を定義してから、ポインターをクリックし、ドラッグして目的の曲線を作成します。

 パスを閉じる場合は、線上の最初の点をクリックします。

### <a name="change-the-shape-of-a-curve"></a>曲線のシェイプの変更
 **[個別選択]** ツール ![個別選択ツール](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png) を使用します。

 図形をクリックしてから、図形の任意のポイントをドラッグして曲線の形状を変更します。

### <a name="draw-a-free-form-path"></a>フリーハンドのパスの描画
 **[鉛筆]** ツール ![鉛筆ツール](../designers/media/509dc167-734f-46c9-b012-987ee63450cd.png) を使用します。

 アートボード上で、実際の鉛筆のように自由にパスを描画できます。

### <a name="remove-part-of-a-path"></a>パスの一部の削除
 **[個別選択]** ツール ![個別選択ツール](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png) を使用します。

 削除する部分を含むパスを選択して、 **[削除]** ボタンをクリックします。

### <a name="remove-a-point-in-a-path"></a>パス内のポイントの削除
 **[選択]** ツール ![選択ツール](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png) と **[ペン]** ツール ![ペン ツール](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png) を使用します。

 **[選択]** ツール ![選択ツール](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png) を使用してパスを選択します。 次に、**[ペン]** ツール ![ペン ツール](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png) を使用して、削除するポイントをクリックします。

### <a name="add-a-point-to-a-path"></a>パスへのポイントの追加
 **[選択]** ツール ![選択ツール](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png) と **[ペン]** ツール ![ペン ツール](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png) を使用します。

 **[選択]** ツール ![選択ツール](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png) を使用してパスを選択します。 **[ペン]** ツール ![ペン ツール](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png) を使用して、ポイントを追加するパス上の任意の場所をクリックします。

##  <a name="Convert"></a> 図形のパスへの変換
 パスを変更するのと同じ方法で図形を変更するには、図形をパスに変換します。

 **短いビデオを見る:**![インストール済みフィーチャーの構成](../designers/media/bldadminconsoleinitialconfigicon.png) [パスの作業:図形をパスに変換する](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147)。

##  <a name="Combine"></a> パスの結合
 パスと図形を結合して 1 つのパスにすることができます。

 ![パスの結合](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png)

|||||
|-|-|-|-|
|![結合前の 2 つの図形](../designers/media/b1_1.png)|結合前の 2 つの図形|![交差](../designers/media/b1_4.png)|交差|
|![重複部分を除外](../designers/media/b1_2.png)|合算|![](../designers/media/b1_5.png)|重複部分を除外|
|![減算](../designers/media/b1_3.png)|除算|![](../designers/media/b1_6.png)|減算|

 **短いビデオを見る:**![インストール済みフィーチャーの構成](../designers/media/bldadminconsoleinitialconfigicon.png) [パスの作業:パスを結合する](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195)。

##  <a name="Compound"></a> 複合パスの作成
 複合パスを作成するときは、パスの交差している部分が減算されます。複合後のパスのビジュアル プロパティは、最背面にあったパスと同じになります。

 複合パスは、作成後はいつでも分離できます。

 ![複合パスを分離する](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png)

 **短いビデオを見る:**![インストール済みフィーチャーの構成](../designers/media/bldadminconsoleinitialconfigicon.png) [パスの作業:複合パスを作成する](https://www.youtube.com/watch?v=Io5bC0-nH6Q)。

##  <a name="Clipping"></a> クリッピング パスの作成
 クリッピング パスは、別のオブジェクトに適用するパスまたは図形です。クリッピング パスの外側のオブジェクトがマスクされて非表示になります。

 ![クリッピング パス](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png)

 **短いビデオを見る:**![インストール済みフィーチャーの構成](../designers/media/bldadminconsoleinitialconfigicon.png) [パスの作業:クリッピング パスを作成する](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232)。

## <a name="see-also"></a>関連項目

- [Blend for Visual Studio を使用して UI を作成する](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)