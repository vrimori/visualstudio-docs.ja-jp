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
ms.openlocfilehash: 7e911686d1f8bff191c439f4fc2b92c37d60a31f
ms.sourcegitcommit: 38097344f3ff74ba7b03bcfa45910015ca6bc2be
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2017
---
1.  デバイスまたはサーバーをデバッグするコンピューターではなく Visual Studio を実行しているコンピューター)、リモート ツールの正しいバージョンを取得します。

    |Version|リンク|メモ|
    |-|-|-|
    |Visual Studio 2017 バージョン 15.5|[リモート ツール](https://www.visualstudio.com/downloads/#remote-tools-for-visual-studio-2017)|常に、デバイスのオペレーティング システム (x86 または x64) に一致するバージョンをダウンロードします。 強化されたセキュリティ モードが有効な場合 (Windows Server)、指示された場合は新しい信頼できるサイトを追加する必要があります。|
    |Visual Studio 2017 年 (古い)|[リモート ツール](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|以前のリリースの Visual Studio 2017 用のリモート ツール My.VisualStudio.com から利用できます。メッセージが表示されたら、結合、無料の Visual Studio Dev Essentials グループ、または、Visual Studio サブスクリプションでサインインします。 id です。 強化されたセキュリティ モードが有効な場合 (Windows Server)、指示された場合は新しい信頼できるサイトを追加する必要があります。|
    |Visual Studio 2015 更新プログラム 3|[リモート ツール](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|メッセージが表示されたら、結合、無料の Visual Studio Dev Essentials グループ、または、Visual Studio サブスクリプションでサインインします。 id です。 強化されたセキュリティ モードが有効な場合 (Windows Server)、指示された場合は新しい信頼できるサイトを追加する必要があります。|
    |Visual Studio 2015 が (古い)|[リモート ツール](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|メッセージが表示されたら、結合、無料の Visual Studio Dev Essentials グループ、または、Visual Studio サブスクリプションでサインインします。 id です。 強化されたセキュリティ モードが有効な場合 (Windows Server)、指示された場合は新しい信頼できるサイトを追加する必要があります。|
    |Visual Studio 2013|[リモート ツール](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Visual Studio 2013 のドキュメント内のページをダウンロードします。|
    |Visual Studio 2012|[リモート ツール](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Visual Studio 2012 のドキュメント内のページをダウンロードします。|
  
2.  [ダウンロード] ページで、(x 86、x64、または ARM) は、オペレーティング システムに一致するバージョンのツールを選択し、リモート ツールをダウンロードします。
  
    > [!IMPORTANT]
    >  Visual Studio のバージョンに一致する remote tools の最新バージョンをインストールすることをお勧めします。 バージョンの不一致は推奨されません。 さらをインストールするオペレーティング システムと同じアーキテクチャを持つリモート ツールをインストールする必要があります。 つまり、64 ビット オペレーティング システムを実行しているリモート コンピューター上の 32 ビット アプリケーションをデバッグする場合は、リモート コンピューターでリモート ツールの 64 ビット バージョンをインストールする必要があります。 
    >   
    >  画面 3 が ARM から x64 に切り替えるアーキテクチャ。 リモート ツールの ARM バージョンでは、Visual Studio 2017 を使用できません。 Visual Studio 2015 では、Visual Studio 2015 RTW ダウンロードで ARM バージョンを探します。
  
3.  実行可能ファイルのダウンロードが完了したら、次のセクションに移動し、セットアップの指示に従います。

リモート コンピューターにリモート デバッガー (msvsmon.exe) をコピーし、実行しようとする場合は注意している、**リモート デバッガー構成ウィザード**(**rdbgwiz.exe**) をダウンロードする場合にのみがインストールされている、ツールです。 特にリモート デバッガーをサービスとして実行する場合は、ウィザードを使用して、後で構成する必要があります。 詳細については、次を参照してください。 [(省略可能)、リモート デバッガーの構成をサービスとして](../../debugger/remote-debugging.md#bkmk_configureService)です。