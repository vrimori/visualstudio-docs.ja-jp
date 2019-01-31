---
title: インストールの場所を選択する
description: ダウンロード キャッシュ、共有コンポーネント、SDK、ツールの場所を異なるドライブに変更することによって、ご利用のシステム ドライブの Visual Studio インストール占有領域を減らす方法について説明します。
ms.date: 11/07/2018
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 522b27093c97101df66aca2e5b4d969bcdaa3bc5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55003240"
---
# <a name="select-the-installation-locations-in-visual-studio-2017"></a>Visual Studio 2017 でインストールの場所を選択する

**15.7 の新機能**:一部のファイル用の場所を変更することで、ご利用のシステム ドライブ上の Visual Studio のインストール占有領域を減らせるようになりました。 具体的には、ダウンロード キャッシュ、共有コンポーネント、SDK、およびツールのファイルに異なる場所を使用できます。

   > [!NOTE]
   > 一部のツールと SDK では、インストールできる場所に関するルールが異なります。 これらのツールおよび SDK は、お客様が別の場所を選択した場合でも、ご利用のシステム ドライブにインストールされます。

開始するには、 ここではその方法を説明します。

1. Visual Studio をインストールするときに、**[インストールの場所]** タブを選びます。

   ![Visual Studio 2017 - インストールの場所を選択する](media/vs-installation-locations.png "インストールの場所を選択します。")

1. **[Visual Studio IDE]** セクションで、既定値をそのまま使います。 Visual Studio では、コア製品がインストールされ、このバージョンの Visual Studio に固有のファイルが含まれます。

   ![[インストールの場所] タブの [Visual Studio IDE] セクション](media/vs-installation-locations-ide.png "[インストールの場所] タブの [Visual Studio IDE] セクションで既定値を受け入れます。")

   > [!TIP]
   > システム ドライブがソリッドステート ドライブ (SSD) の場合は、ご利用のシステム ドライブ上の既定の場所をそのまま使用することをお勧めします。 その理由は、 Visual Studio を使って開発する場合、多くのファイルに対して読み取り、書き込みを行うからです。これにより、ディスク I/O アクティビティが増加します。 最も速いドライブで負荷を処理するのが最善の選択です。

1. **[ダウンロード キャッシュ]** セクションで、ダウンロード キャッシュを保持するかどうかを決定し、そのファイルを格納する場所を決定します。

     ![[インストールの場所] タブの [ダウンロード キャッシュ] セクション](media/vs-installation-locations-cache.png "インストール後にダウンロード キャッシュを保持するかどうかを選び、ファイルを格納するドライブを指定します。")

    1. **[インストール後にダウンロード キャッシュを保持します]** をオンまたはオフにします。

       ダウンロード キャッシュを保持しない場合は、場所は一時的にのみ使われます。 このアクションにより、以前のインストールのファイルが影響を受けたり、削除されたりすることはありません。

    1. ダウンロード キャッシュから、インストール ファイルとマニフェストを格納するドライブを指定します。

        たとえば、"C++ によるデスクトップ開発" ワークロードを選ぶと、システム ドライブで一時的に 1.58 GB が必要になり、インストールが完了するとすぐに解放されます。

       > [!IMPORTANT]
       > この場所は最初のインストール時に設定され、後でインストーラー UI から変更することはできません。 ダウンロード キャッシュを移動するには、代わりに、[コマンド ライン パラメーターを使用する](use-command-line-parameters-to-install-visual-studio.md)必要があります。

1. **[共有コンポーネント、ツール、SDK]** セクションで、サイドバイサイド Visual Studio インストールによって共有されるファイルを格納するドライブを指定します。 また、SDK とツールはこのディレクトリにも格納されます。

   ![[インストールの場所] タブの [共有コンポーネント、ツール、SDK] セクション](media/vs-installation-locations-shared.png "共有コンポーネント、ツール、SDK を格納する場所を指定します。")

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>関連項目

* [Visual Studio 2017 のインストール](install-visual-studio.md)
* [Visual Studio 2017 の更新](update-visual-studio.md)
* [Visual Studio 2017 の変更](update-visual-studio.md)
* [Visual Studio 2017 のアンインストール](uninstall-visual-studio.md)
