---
title: リモート デバッガーのダウンロード
description: リモート デバッガーのダウンロード リンク
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 987193cb7f78947087c6d387e16261d83a20e7c2
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809247"
---
1.  デバイスまたはサーバーをデバッグするコンピューター (はなく Visual Studio を実行しているコンピューター) 上には、リモート ツールの適切なバージョンを取得します。

    |Version|リンク|メモ|
    |-|-|-|
    |Visual Studio 2017 (最新バージョン)|[リモート ツール](https://visualstudio.microsoft.com/downloads/?q=remote+tools#remote-tools-for-visual-studio-2017)|常に、デバイスのオペレーティング システム (x 86、x64、または ARM64 など) に一致するバージョンをダウンロードします。 Windows Server で、次を参照してください。[ファイルのダウンロードをブロック解除](../../debugger/remote-debugging.md#unblock_msvsmon)については、リモート ツールをダウンロードします。|
    |Visual Studio 2017 が (古い)|[リモート ツール](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Remote tools for Visual Studio 2017 の以前のリリースを My.VisualStudio.com から入手できます。 結合の無料の Visual Studio Dev Essentials のグループ、または Visual Studio サブスクリプションでサインインが id。 メッセージが表示されたら、 Windows Server で、次を参照してください。[ファイルのダウンロードをブロック解除](../../debugger/remote-debugging.md#unblock_msvsmon)については、リモート ツールをダウンロードします。|
    |(古い) の visual Studio 2015|[リモート ツール](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|結合の無料の Visual Studio Dev Essentials のグループ、または Visual Studio サブスクリプションでサインインが id。 メッセージが表示されたら、 Windows Server で、次を参照してください。[ファイルのダウンロードをブロック解除](../../debugger/remote-debugging.md#unblock_msvsmon)については、リモート ツールをダウンロードします。|
    |Visual Studio 2013|[リモート ツール](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Visual Studio 2013 のドキュメント内のページをダウンロードします。|
    |Visual Studio 2012|[リモート ツール](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Visual Studio 2012 のドキュメント内のページをダウンロードします。|

2.  [ダウンロード] ページで、オペレーティング システム (x86、x64、ARM、または ARM64) と一致するバージョンのツールを選択し、リモート ツールをダウンロードします。

    > [!IMPORTANT]
    >  Visual Studio のバージョンに一致する remote tools の最新バージョンをインストールすることをお勧めします。 一致しないバージョンは推奨されません。 さらをインストールするオペレーティング システムと同じアーキテクチャを持つリモート ツールをインストールする必要があります。 つまり、64 ビットのオペレーティング システムを実行しているリモート コンピューター上の 32 ビット アプリケーションをデバッグする場合は、リモート コンピューターのリモート ツールの 64 ビット バージョンをインストールする必要があります。
    >
    >  ARM デバイスで Windows 10 でのデバッグ、リモート ツールの最新バージョンで ARM64 のダウンロードを選択します。  Windows RT デバイスの場合に、Visual Studio 2015 の RTW ダウンロードで使用可能なだけ ARM バージョンを選択します。

3.  実行可能ファイルのダウンロードが完了したら、次のセクションに移動し、セットアップの指示に従います。

リモートのコンピューターにリモート デバッガー (msvsmon.exe) をコピーし、実行しようとする場合がありますが、**リモート デバッガー構成ウィザード**(**rdbgwiz.exe**) をダウンロードする場合にのみがインストールされている、ツールです。 特に、リモート デバッガーをサービスとして実行する場合は、後で、構成ウィザードを使用する必要があります。 詳細については、次を参照してください。 [(省略可能) 構成サービスとしてリモート デバッガー](../../debugger/remote-debugging.md#bkmk_configureService)します。
