---
title: '方法: Mipmap を含むテクスチャをエクスポートする |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 732fa9a5d32916545b281a006cbeeaa93771f3ec
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54754337"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>方法: ミップマップを含むテクスチャをエクスポートする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

イメージ コンテンツ パイプラインは、プロジェクトのビルド フェーズ中にソース イメージから MIPMAP を生成できます。 各 MIPMAP レベルのイメージの内容を手動で指定する必要がない場合 (特定の効果を得るためになど)、ビルド時に MIPMAP を生成することで、MIPMAP の内容とソース テクスチャが確実に同期するようになります。また、実行時に MIPMAP を生成するためのパフォーマンス コストがゼロになります。  
  
 このドキュメントでは、以下のアクティビティについて説明します。  
  
-   イメージ コンテンツ パイプラインによって処理されるようにソース イメージを構成する。  
  
-   MIPMAP を生成するようにイメージ コンテンツ パイプラインを構成する。  
  
## <a name="exporting-mipmaps"></a>MIPMAP のエクスポート  
 MIPMAP には、3D ゲームやアプリのテクスチャ サーフェス用に自動調整される画面領域詳細レベルがあります。 このレベルによりゲームやアプリのレンダリング パフォーマンスが向上します。テクスチャのダウンサンプリング バージョンが前計算されて、テクスチャ全体をサンプリングするたびにダウンサンプリングする必要がなくなるためです。  
  
#### <a name="to-export-a-texture-that-has-mipmaps"></a>MIPMAP を含むテクスチャをエクスポートするには  
  
1. 基本的なテクスチャを作成します。 既存のイメージ ファイルを読み込むか、「[方法:基本的なテクスチャを作成する](../designers/how-to-create-a-basic-texture.md) MIPMAP をサポートするには、テクスチャの幅と高さを 2 の累乗の同じサイズ (64x64、256x256、512x512 など) に指定します。  
  
2. イメージ コンテンツ パイプラインによって処理されるように、前の手順で作成したテクスチャ ファイルを構成します。 **ソリューション エクスプローラー**で、先ほど作成したテクスチャ ファイルのショートカット メニューを開き、**[プロパティ]** をクリックします。 **[構成プロパティ]** の **[全般]** ページで、**[項目の種類]** を **[Image Content Pipeline]** (イメージ コンテンツ パイプライン) に設定します。 **[コンテンツ]** が **[はい]** に、**[ビルドから除外]** が **[いいえ]** に設定されていることを確認し、**[適用]** ボタンをクリックします。 **[イメージ コンテンツ パイプライン]** の構成プロパティ ページが表示されます。  
  
3. MIPMAP を生成するように、イメージ コンテンツ パイプラインを構成します。 **[構成プロパティ]** で、**[Image Content Pipeline]** \(イメージ コンテンツ パイプライン\)、**[全般]** ページの順にクリックし、**[MIPS の生成]** を **[はい (/generatemips)]** に設定します。  
  
4. **[OK]** を選択します。  
  
   プロジェクトをビルドすると、イメージ コンテンツ パイプラインによってソース イメージは作業形式から、指定した出力形式に変換されます。同時に、MIPMAP レベルが生成されます。結果はプロジェクトの出力ディレクトリにコピーされます。
