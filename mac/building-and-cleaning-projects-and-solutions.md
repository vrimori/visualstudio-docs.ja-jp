---
title: Visual Studio for Mac でのプロジェクトとソリューションのビルドとクリーン
description: この記事では、Visual Studio for Mac でプロジェクトをビルドする方法について説明します
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: E4B6CB42-9FE2-43B9-93B7-BD4BD50518B1
ms.openlocfilehash: 74a78c5cb4e9583db1eb99bb6eeb5691cb4adcfd
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294241"
---
# <a name="building-and-cleaning-projects-and-solutions"></a>プロジェクトとソリューションのビルドおよびクリーン

この記事の手順に従うと、ソリューションとプロジェクトのビルド、リビルド、クリーンの方法が理解できます。

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>ソリューション全体のビルド、リビルド、またはクリーン

ソリューション全体のビルド、リビルド、またはクリーン:

1. Solution Pad でソリューション ノードを選択します。

    ![ソリューション ノードの選択](media/compiling-and-building-image1.png)

2. メニュー バーで [ビルド] メニューを選択し、次のいずれかのオプションを選択します。

    ![[すべてビルド] メニュー項目の選択](media/compiling-and-building-image2.png)

    * **すべてビルド** - 一番新しいビルド以降、プロジェクト内で変更された、プロジェクト内のすべてのファイルがビルドされます。
    * **すべてリビルド** - ソリューションを取り除き、それからビルドします。
    * **すべてクリーン** - ソリューションからすべてのビルド製品を削除します。

## <a name="to-build-or-rebuild-a-single-project"></a>1 つのプロジェクトをビルドまたはリビルドするには

1. Solution Pad で、プロジェクトを選択します。

2. メニュー バーで、[ビルド] を選択し、[<プロジェクト名> のビルド]、[<プロジェクト名> のリビルド]、[<プロジェクト名> のクリーン] のいずれかを選択します。

## <a name="to-stop-a-build"></a>ビルドを停止するには

ビルドを停止するには、ステータス領域の赤い正方形を押します。

![赤い正方形を押し、ビルドを停止する](media/compiling-and-building-image3.png)

## <a name="see-also"></a>関連項目

- [プロジェクトとソリューションのビルドおよびクリーン (Windows の Visual Studio)](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)