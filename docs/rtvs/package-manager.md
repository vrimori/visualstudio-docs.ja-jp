---
title: "R Tools for Visual Studio のパッケージ マネージャー | Microsoft Docs"
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93accb9a-1ef8-4806-baa4-02477c2d7ef0
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: a0bc08a5b4e38651e8d62629778e3ab1647e1bcb
ms.contentlocale: ja-jp
ms.lasthandoff: 05/12/2017

---


# <a name="package-manager"></a>パッケージ マネージャー

R Tools for Visual Studio (RTVS) パッケージ マネージャーは R パッケージを管理するための UI です。 **[R Tools]、[Windows]、[パッケージ]** の順に選択するか、Ctrl + 7 を押すと開きます。

パッケージ マネージャーには、下の説明にあるような 3 つのタブがあります。 すべてのタブの左側に関連パッケージの一覧が、右側に選択したパッケージの詳細が表示されます。詳細として、パッケージのバージョン、説明、ライセンス、インストール場所、他の関連情報のリンクなどあります。 右上の検索ボックスで一覧を絞り込めます。

> [!Tip]
> 検索ボックスの条件は、タブを切り替えても有効のままです。

- **[使用可能]** では、インストールするパッケージを閲覧できます。 パッケージが既にインストールされている場合、右の **[インストール]** ボタンが **[アンインストール]** に変わります。

    ![R Tools for Visual Studio パッケージ マネージャーの利用可能なパッケージのタブ](~/rtvs/media/package-manager-available.png)

- **[インストール済み]** には、インストールされ、読み込まれたパッケージがすべて表示されます。 パッケージの横にある緑の丸印は、それが R セッションに読み込まれていることを示します。 左側の一覧にある赤い X 印アイコンまたは右側の **[アンインストール]** ボタンでパッケージをアンインストールできます。 インストール済みパッケージの右にある青い上向き矢印をクリックすると、新しいバージョンが存在する場合、パッケージが更新されます。

    ![R Tools for Visual Studio パッケージ マネージャーのインストール済みパッケージのタブ](~/rtvs/media/package-manager-installed.png)

- **[読み込み]** には、R セッションに読み込まれているパッケージのみが表示されます。そのため、すべてのパッケージに緑の丸印が付きます。 ここでパッケージをアンインストールしたり、更新したりすることもできます。

    ![R Tools for Visual Studio パッケージ マネージャーの読み込み済みパッケージのタブ](~/rtvs/media/package-manager-loaded.png)

## <a name="package-locations"></a>パッケージの場所

パッケージは次の場所にインストールされます。

- RTVS に含まれるコア パッケージは `C:\Program Files\Microsoft\R Client\R_SERVER\library` にインストールされます。
- 追加パッケージは `%userprofile%\Documents\R\win-library\3.3` にインストールされます。

