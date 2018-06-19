---
title: Visual Studio 2017 でインストールの場所を変更する
description: ダウンロード キャッシュ、共有コンポーネント、SDK、ツールの場所を異なるドライブに変更することによって、システム ドライブのインストール占有領域を減らす方法について説明します。
ms.date: 05/07/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- move installation files to different drives
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eef4f8b66da517e471a25bb36e777f6cc343b0a3
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "33995781"
---
# <a name="change-the-installation-locations-in-visual-studio-2017"></a>Visual Studio 2017 でインストールの場所を変更する

**15.7 の新機能**: ダウンロード キャッシュ、共有コンポーネント、SDK、ツールを異なるドライブに移動することによって、システム ドライブのインストール占有領域を減らすことができます。

ここではその方法を説明します。

1. Visual Studio をインストールするときに、**[インストール オプション]** タブを選びます。

  ![Visual Studio 2017 - インストール場所を変更する](media/installation-options-by-location.png "インストール場所を変更する")

  > [!IMPORTANT]
  > インストールをいったん中断し、後で再開した場合、Visual Studio により中断した場所から開始されます。 つまり、インストールの進行状況は、まだダウンロードおよびインストールされずに残っているパッケージに適用され、前のカウントからの開始とはなりません。

2. **[Visual Studio IDE]** セクションで、既定値をそのまま使います。 このようにすると、コア製品がインストールされ、このバージョンの Visual Studio に固有のファイルが含まれます。

 > [!IMPORTANT]
 > システム ドライブがソリッドステート ドライブ (SSD) の場合、システム ドライブの既定の場所をそのまま使うことをお勧めします。Visual Studio で開発を行うと、多くのファイルの読み書きが行われ、ディスク I/O 動作が増加するためです。  最も速いドライブで負荷を処理するのが最善の選択です。

2. **[ダウンロード キャッシュ]** セクションで、ダウンロード キャッシュを保持するかどうかを決定し、それに応じて **[インストール後にダウンロード キャッシュを保持します]** をオンまたはオフにします。 <br><br>ダウンロード キャッシュを保持しない場合は、場所は一時的にのみ使われます。 また、この操作により、以前のインストールのファイルが影響を受けたり、削除されたりすることはありません (すべてのインストール パッケージを消去するには、以前のインストールを個別に変更する必要があります)。

3. **[ダウンロード キャッシュ]** セクションで、インストール ファイルとマニフェストを格納するドライブを指定します。 <br><br>たとえば、"C++ によるデスクトップ開発" ワークロードを選ぶと、システム ドライブで一時的に 1.58 GB が必要になり、インストールが完了するとすぐに解放されます。

 > [!NOTE]
 > ファイルは最初にシステム ドライブ上の一時フォルダーにダウンロードされ、Visual Studio がファイルを検証してダウンロード キャッシュ フォルダーに移動した後に、削除されます。 別のドライブにダウンロード キャッシュを保持することを選んだ場合でも、システム ドライブ上のダウンロード キャッシュと同じサイズが、ディスク領域に必要です。
 > [!IMPORTANT]
 > 場所は最初のインストール時に設定され、後でインストーラー UI から変更することはできません。 ダウンロード キャッシュを移動するには、代わりに[コマンド ライン パラメーターを使用する](use-command-line-parameters-to-install-visual-studio.md)必要があります

4. **[共有コンポーネント、ツール、SDK]** セクションで、サイド バイ サイド Visual Studio インストールによって共有されるファイルを格納するドライブを指定します。 Visual Studio インストーラーがインストール場所を変更する SDK とツールも、このディレクトリに格納されます。

 > [!NOTE]
 > 一部のツールと SDK では、インストールできる場所に関するルールが異なります。 これらのツールおよび SDK は、ユーザーが別の場所を選択した場合でも、システム ドライブにインストールされます。

## <a name="get-support"></a>サポートを受ける

ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング](troubleshooting-installation-issues.md)」ページのヘルプをご覧ください。 インストールに関しては、[ライブ チャット](https://www.visualstudio.com/vs/support/#talktous) (英語のみ) によってもお問い合わせいただけます。詳細については、[Visual Studio のお問い合わせページ](https://www.visualstudio.com/vs/support/#talktous)を参照してください。

他のいくつかのサポート オプションを次に示します。

* Visual Studio インストーラーおよび Visual Studio IDE の両方に表示される [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから、製品の問題を Microsoft に報告できます。
* [UserVoice](https://visualstudio.uservoice.com/forums/121579) で、製品に関する提案を投稿できます。
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、回答を検索したりできます。
* [Gitter コミュニティの Visual Studio に関するスレッド](https://gitter.im/Microsoft/VisualStudio)で、Microsoft や他の Visual Studio 開発者と情報を交換することもできます。 (このオプションでは [GitHub](https://github.com/) アカウントが必要になります)。

## <a name="see-also"></a>関連項目

* [Visual Studio 2017 のインストール](install-visual-studio.md)
* [Visual Studio 2017 の更新](update-visual-studio.md)
* [Visual Studio 2017 の変更](update-visual-studio.md)
* [Visual Studio 2017 のアンインストール](uninstall-visual-studio.md)
