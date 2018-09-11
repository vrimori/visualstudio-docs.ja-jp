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
ms.openlocfilehash: a9867acf2a0877322b85d25c3af781ccfdd3f58c
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44343150"
---
1.  デバイスまたはサーバーをデバッグするコンピューター (はなく Visual Studio を実行しているコンピューター) 上には、リモート ツールの適切なバージョンを取得します。

    |Version|リンク|メモ|
    |-|-|-|
    |Visual Studio 2017 (最新バージョン)|[リモート ツール](https://visualstudio.microsoft.com/downloads/?q=remote+tools#remote-tools-for-visual-studio-2017)|リモート ツールの最新バージョンは、すべての Visual Studio 2017 リリースと互換性が。 常に、デバイスのオペレーティング システム (x 86、x64、または ARM64 など) に一致するバージョンをダウンロードします。 Windows Server で、次を参照してください。[ファイルのダウンロードをブロック解除](../../debugger/remote-debugging-unblock-file-download.md)については、リモート ツールをダウンロードします。|
    |Visual Studio 2015|[リモート ツール](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Visual Studio 2015 用リモート ツール My.VisualStudio.com から利用できます。 メッセージが表示されたら、結合、無料[Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/)プログラム、または、Visual Studio のサブスクリプション ID でサインイン Windows Server で、次を参照してください。[ファイルのダウンロードをブロック解除](../../debugger/remote-debugging-unblock-file-download.md)については、リモート ツールをダウンロードします。|
    |Visual Studio 2013|[リモート ツール](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#Installing_the_Remote_Tools)|Visual Studio 2013 のドキュメント内のページをダウンロードします。|
    |Visual Studio 2012|[リモート ツール](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#BKMK_Installing_the_Remote_Tools)|Visual Studio 2012 のドキュメント内のページをダウンロードします。|

2.  [ダウンロード] ページで、オペレーティング システム (x86、x64、ARM、または ARM64) と一致するバージョンのツールを選択し、リモート ツールをダウンロードします。

    > [!IMPORTANT]
    >  Visual Studio のリリースの remote tools の最新バージョンをインストールすることをお勧めします。 最新バージョン (たとえば、15.8) 以前のリリース (たとえば、15.0); と互換性がただし、以前のバージョンでは、以降のリリースと互換性がありません。 さらをインストールするオペレーティング システムと同じアーキテクチャを持つリモート ツールをインストールする必要があります。 つまり、64 ビットのオペレーティング システムを実行しているリモート コンピューター上の 32 ビット アプリケーションをデバッグする場合は、リモート コンピューターのリモート ツールの 64 ビット バージョンをインストールする必要があります。
    >
    >  ARM デバイスで Windows 10 でのデバッグ、リモート ツールの最新バージョンで ARM64 のダウンロードを選択します。  Windows RT デバイスの場合に、Visual Studio 2015 の RTW ダウンロードで使用可能なだけ ARM バージョンを選択します。

3.  実行可能ファイルのダウンロードが完了したら、次のセクションに移動し、セットアップの指示に従います。

リモートのコンピューターにリモート デバッガー (msvsmon.exe) をコピーし、実行しようとする場合がありますが、**リモート デバッガー構成ウィザード**(**rdbgwiz.exe**) をダウンロードする場合にのみがインストールされている、ツールです。 特に、リモート デバッガーをサービスとして実行する場合は、後で、構成ウィザードを使用する必要があります。 詳細については、次を参照してください。 [(省略可能) 構成サービスとしてリモート デバッガー](../../debugger/remote-debugging.md#bkmk_configureService)します。
