---
title: R のパッケージ マネージャー
description: Visual Studio の R パッケージ マネージャーを使って R パッケージをインストールおよび管理する方法について説明します。
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 966a05e0b339409a5dc4df247b4ea2101a8a768d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922848"
---
# <a name="package-manager"></a>パッケージ マネージャー

R Tools for Visual Studio (RTVS) パッケージ マネージャーは R パッケージを管理するための UI です。 **[R Tools]** > **[Windows]** > **[パッケージ]** の順に選択するか、**Ctrl **+** 7** キーを押すと開きます。

パッケージ マネージャーには、3 つのタブがあります。 それぞれのタブの左側に関連パッケージの一覧が、右側に選択したパッケージの詳細が表示されます。詳細として、パッケージのバージョン、説明、ライセンス、インストール場所、他の関連情報のリンクなどがあります。 右上の検索ボックスで一覧を絞り込めます。

> [!Tip]
> 検索ボックスの条件は、タブを切り替えても有効のままです。

- **[使用可能]** では、インストールするパッケージを閲覧できます。 パッケージが既にインストールされている場合、右の **[インストール]** ボタンが **[アンインストール]** に変わります。

    ![R Tools for Visual Studio パッケージ マネージャーの利用可能なパッケージのタブ](media/package-manager-available.png)

- **[インストール済み]** には、インストールされ、読み込まれたパッケージがすべて表示されます。 パッケージの横にある緑の丸印は、それが R セッションに読み込まれていることを示します。 左側の一覧にある赤い X 印アイコンまたは右側の **[アンインストール]** ボタンでパッケージをアンインストールできます。 インストール済みパッケージの新しいバージョンがある場合、パッケージの右側にある青い上向き矢印をクリックすると更新が実行されます。

    ![R Tools for Visual Studio パッケージ マネージャーのインストール済みパッケージのタブ](media/package-manager-installed.png)

- **[読み込み]** には、R セッションに読み込まれているパッケージのみが表示されます。すべてのパッケージに緑の丸印が付きます。 ここでパッケージをアンインストールしたり、更新したりすることもできます。

    ![R Tools for Visual Studio パッケージ マネージャーの読み込み済みパッケージのタブ](media/package-manager-loaded.png)

## <a name="package-locations"></a>パッケージの場所

パッケージは次の場所にインストールされます。

- RTVS に含まれるコア パッケージは *C:\Program Files\Microsoft\R Client\R_SERVER\library* にインストールされます。
- 追加パッケージは *%userprofile%\Documents\R\win-library\3.3* にインストールされます。
