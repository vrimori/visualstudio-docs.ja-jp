---
title: "R Tools for Visual Studio のパッケージ マネージャー | Microsoft Docs"
ms.custom: 
ms.date: 06/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 92644bcb21c23eb91ccd8223b99cce98ba4c57db
ms.sourcegitcommit: ae9450e81c4167b3fbc9ee5d1992fc693628eafa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2017
---
# <a name="package-manager"></a>パッケージ マネージャー

R Tools for Visual Studio (RTVS) パッケージ マネージャーは R パッケージを管理するための UI です。 **[R Tools]、[Windows]、[パッケージ]** の順に選択するか、Ctrl + 7 を押すと開きます。

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

- RTVS に含まれるコア パッケージは `C:\Program Files\Microsoft\R Client\R_SERVER\library` にインストールされます。
- 追加パッケージは `%userprofile%\Documents\R\win-library\3.3` にインストールされます。
