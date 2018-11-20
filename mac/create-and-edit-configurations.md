---
title: ビルド構成の作成と編集
description: この記事では、Visual Studio for Mac でビルド構成を作成する方法について説明します。
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: CC1B72D6-12FF-4CCC-A9D4-00F2DC14589F
ms.openlocfilehash: 49a64f7752bc5f6b3dbbb0dcfed385bfdd5ef9be
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296100"
---
# <a name="creating-and-editing-build-configurations"></a>ビルド構成の作成と編集

ビルド構成は、個々のプロジェクトに対して作成するか、ソリューション全体に対して作成できます。 これらの構成によりビルドを正確に制御できます。

プロジェクトとソリューションの両方のオプション メニューには、新しい構成と既存の構成を作成し、編集するための領域があります。

## <a name="creating-a-project-build-configurations"></a>プロジェクトのビルド構成の作成

プロジェクトのビルド構成は次の手順で作成します。

1. プロジェクト ノードを右クリックし、**[オプション]** を選択します。

2. [プロジェクト オプション] ダイアログで、**[ビルド]、[構成]** の順に選択します。

    ![プロジェクト オプションの構成マネージャー](media/create-and-edit-configurations-image2.png)

3. 新しい構成を作成するには、**[追加]** を選択します。 あるいは、既存の構成の 1 つをコピーできます。

構成が作成されたら、プロジェクト オプションの **[ビルド]** セクションを利用し、構成に合わせてプロパティを調整できます。

![ビルド オプションの構成](media/create-and-edit-configurations-image3.png)

## <a name="creating-a-solution-build-configuration"></a>ソリューションのビルド構成の作成

ソリューションのビルド構成は次の手順で作成します。

1. ソリューション ノードを右クリックし、**[オプション]** を選択します。

2. [ソリューション オプション] ダイアログで、**[ビルド]、[構成]** の順に選択します。

    ![ソリューション オプションの構成マネージャー](media/create-and-edit-configurations-image1.png)

3. 新しい構成を作成するには、**[追加]** を選択します。 あるいは、既存の構成の 1 つをコピーできます。

構成が作成されたら、各プロジェクトのオプションの **[ビルド]** セクションを利用し、構成に合わせてプロパティを調整できます。

![ビルド オプションの構成](media/create-and-edit-configurations-image3.png)

## <a name="editing-a-build-configuration"></a>ビルド構成の編集

構成の名前を変更するには、プロジェクトまたはソリューション オプションの構成一覧から構成を選択します。

![構成一覧](media/create-and-edit-configurations-image4.png)

**[名前の変更]** ボタンを選択します。

![[名前の変更] ダイアログ](media/create-and-edit-configurations-image5.png)

## <a name="see-also"></a>関連項目

- [ビルド構成を作成して編集する (Windows の Visual Studio)](/visualstudio/ide/how-to-create-and-edit-configurations)