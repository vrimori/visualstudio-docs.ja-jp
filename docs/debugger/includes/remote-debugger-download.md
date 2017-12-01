---
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
ms.openlocfilehash: 109d9d8718a2c46dbd982e58b22dcf43e55b2205
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/29/2017
---
1.  デバイスまたはサーバーをデバッグするコンピューターではなく Visual Studio を実行しているコンピューター)、リモート ツールの正しいバージョンを取得します。

    |バージョン|Link|ノート|
    |-|-|-|
    |Visual Studio 2017 Update 4|[リモート ツール](https://www.visualstudio.com/downloads/#remote-tools-for-visual-studio-2017)|常に、デバイスのオペレーティング システム (x86 または x64) に一致するバージョンをダウンロードします。 古いバージョンのブラウザーの直接リンクを使用して:[リモート ツール (x64)](https://go.microsoft.com/fwlink/?LinkId=746570&clcid=0x409)と[リモート ツール (x86)](https://go.microsoft.com/fwlink/?LinkId=746569&clcid=0x409)です。|
    |Visual Studio 2017 年 (古い)|[リモート ツール](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|メッセージが表示されたら、無料の Visual Studio Dev Essentials グループに参加または有効な Visual Studio サブスクリプションでサインインすることができます。 古いブラウザーは、指示された場合は、新しい信頼済みサイトを追加する必要があります。|
    |Visual Studio 2015 更新プログラム 3|[リモート ツール](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|メッセージが表示されたら、無料の Visual Studio Dev Essentials グループに参加または有効な Visual Studio サブスクリプションでサインインすることができます。 古いブラウザーは、指示された場合は、新しい信頼済みサイトを追加する必要があります。|
    |Visual Studio 2015 が (古い)|[リモート ツール](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|メッセージが表示されたら、無料の Visual Studio Dev Essentials グループに参加または有効な Visual Studio サブスクリプションでサインインすることができます。 古いブラウザーは、指示された場合は、新しい信頼済みサイトを追加する必要があります。|
    |Visual Studio 2013|[リモート ツール](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Visual Studio 2013 のドキュメント内のページをダウンロードします。|
    |Visual Studio 2012|[リモート ツール](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Visual Studio 2012 のドキュメント内のページをダウンロードします。|
  
2.  [ダウンロード] ページで、(x 86、x64、または ARM) は、オペレーティング システムに一致するバージョンのツールを選択し、リモート ツールをダウンロードします。
  
    > [!IMPORTANT]
    >  Visual Studio のバージョンに一致する remote tools の最新バージョンをインストールすることをお勧めします。 バージョンの不一致は推奨されません。 さらをインストールするオペレーティング システムと同じアーキテクチャを持つリモート ツールをインストールする必要があります。 つまり、64 ビット オペレーティング システムを実行しているリモート コンピューター上の 32 ビット アプリケーションをデバッグする場合は、リモート コンピューターでリモート ツールの 64 ビット バージョンをインストールする必要があります。 
    >   
    >  画面 3 が ARM から x64 に切り替えるアーキテクチャ。 リモート ツールの ARM バージョンでは、Visual Studio 2017 を使用できません。 Visual Studio 2015 では、Visual Studio 2015 RTW ダウンロードで ARM バージョンを探します。
  
3.  実行可能ファイルのダウンロードが完了したら、次のセクションに移動し、セットアップの指示に従います。

リモート コンピューターにリモート デバッガー (msvsmon.exe) をコピーし、実行しようとする場合は注意している、**リモート デバッガー構成ウィザード**(**rdbgwiz.exe**) をダウンロードする場合にのみがインストールされている、ツールです。 特にリモート デバッガーをサービスとして実行する場合は、ウィザードを使用して、後で構成する必要があります。 詳細については、次を参照してください。 [(省略可能)、リモート デバッガーの構成をサービスとして](../../debugger/remote-debugging.md#bkmk_configureService)です。