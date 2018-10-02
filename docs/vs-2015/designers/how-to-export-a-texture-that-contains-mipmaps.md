---
title: '方法: ミップマップを含むテクスチャをエクスポートする | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4a876676eed593bfa06c3e89521522d9901c58ea
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545073"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>方法: ミップマップを含むテクスチャをエクスポートする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: そのミップマップを含むテクスチャをエクスポート](https://docs.microsoft.com/visualstudio/designers/how-to-export-a-texture-that-contains-mipmaps)します。  
  
イメージ コンテンツ パイプラインは、プロジェクトのビルド フェーズ中にソース イメージから MIPMAP を生成できます。 各 MIPMAP レベルのイメージの内容を手動で指定する必要がない場合 (特定の効果を得るためになど)、ビルド時に MIPMAP を生成することで、MIPMAP の内容とソース テクスチャが確実に同期するようになります。また、実行時に MIPMAP を生成するためのパフォーマンス コストがゼロになります。  
  
 このドキュメントでは、以下のアクティビティについて説明します。  
  
-   イメージ コンテンツ パイプラインによって処理されるようにソース イメージを構成する。  
  
-   MIPMAP を生成するようにイメージ コンテンツ パイプラインを構成する。  
  
## <a name="exporting-mipmaps"></a>MIPMAP のエクスポート  
 MIPMAP には、3D ゲームやアプリのテクスチャ サーフェス用に自動調整される画面領域詳細レベルがあります。 このレベルによりゲームやアプリのレンダリング パフォーマンスが向上します。テクスチャのダウンサンプリング バージョンが前計算されて、テクスチャ全体をサンプリングするたびにダウンサンプリングする必要がなくなるためです。  
  
#### <a name="to-export-a-texture-that-has-mipmaps"></a>MIPMAP を含むテクスチャをエクスポートするには  
  
1.  基本的なテクスチャを作成します。 既存のイメージ ファイルを読み込むか、「[方法: 基本テクスチャを作成する](../designers/how-to-create-a-basic-texture.md)」の手順に従ってイメージ ファイルを作成します。 MIPMAP をサポートするには、テクスチャの幅と高さを 2 の累乗の同じサイズ (64x64、256x256、512x512 など) に指定します。  
  
2.  イメージ コンテンツ パイプラインによって処理されるように、前の手順で作成したテクスチャ ファイルを構成します。 **ソリューション エクスプローラー**で、先ほど作成したテクスチャ ファイルのショートカット メニューを開き、**[プロパティ]** をクリックします。 **[構成プロパティ]** の **[全般]** ページで、**[項目の種類]** を **[Image Content Pipeline]** (イメージ コンテンツ パイプライン) に設定します。 **[コンテンツ]** が **[はい]** に、**[ビルドから除外]** が **[いいえ]** に設定されていることを確認し、**[適用]** ボタンをクリックします。 **[イメージ コンテンツ パイプライン]** の構成プロパティ ページが表示されます。  
  
3.  MIPMAP を生成するように、イメージ コンテンツ パイプラインを構成します。 **[構成プロパティ]** で、**[Image Content Pipeline]** \(イメージ コンテンツ パイプライン\)、**[全般]** ページの順にクリックし、**[MIPS の生成]** を **[はい (/generatemips)]** に設定します。  
  
4.  **[OK]** を選択します。  
  
 プロジェクトをビルドすると、イメージ コンテンツ パイプラインによってソース イメージは作業形式から、指定した出力形式に変換されます。同時に、MIPMAP レベルが生成されます。結果はプロジェクトの出力ディレクトリにコピーされます。



