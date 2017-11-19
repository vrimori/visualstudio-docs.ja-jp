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
ms.openlocfilehash: 05a288a2d8dff776d8a5d3faea47b06d101f2ea3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
リモート コンピューターの管理者のアクセス許可が必要です。  
  
1.  リモート デバッガー アプリケーションを探します。 (Msvsmon.exe が記載されて、それがインストールされている場所、または [スタート] メニューを開き、検索**リモート デバッガー**)。
  
     リモート サーバーでリモート デバッガーを実行している場合は、リモート デバッガー アプリケーションを右クリックしを選択することができます**管理者として実行**です。 リモート サーバーで実行しているされない場合、だけ、正常に起動します。
  
3.  初めて (または構成する前に)、リモート ツールを起動すると、**リモート デバッグの構成** ダイアログ ボックスが表示されます。  
  
     ![RemoteDebuggerConfWizardPage](../media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
4.  Windows サービスの API がインストールされていません (Windows Server 2008 R2 でのみ発生します) 場合、は、選択、**インストール**ボタンをクリックします。  
  
5.  リモート ツールで利用される、使用するネットワークの種類を選択します。 少なくとも 1 つのネットワークの種類を選択する必要があります。 コンピューターがドメインを介して接続されている場合は、最初の項目を選択する必要があります。 コンピューターがワークグループまたはホーム グループを介して接続されている場合は、必要に応じて、2 番目または 3 番目の項目を選択する必要があります。  
  
6.  選択**のリモート デバッグ構成**ファイアウォールを構成し、ツールを起動します。  
  
7.  構成が完了すると、リモート デバッガーのウィンドウが表示されます。
  
     ![RemoteDebuggerWindow](../media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
     接続のリモート デバッガーが待機しているようになりました。 サーバー名をメモを行い、これは後で Visual Studio で使用する構成と一致する必要がありますので、表示されている数値をポートです。  
  
 デバッグしリモート デバッガーを停止する必要が終了したらをクリックして**ファイル > 終了**ウィンドウです。 再起動することができます、**開始**メニューまたはコマンドラインから。  
  
 **\<Visual Studio インストール ディレクトリ > \Common7\IDE\Remote Debugger\\< x86、x64、または Appx\msvsmon.exe**です。  