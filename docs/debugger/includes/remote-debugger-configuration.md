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
ms.openlocfilehash: 252c505260986bd08b5522ba79d1e00a82624241
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942960"
---
リモート コンピューターの管理アクセス許可があります。  
  
1. リモート デバッガー アプリケーションを探します。 (これがインストールされている、場所で msvsmon.exe を検索または [スタート] メニューを開き、検索**リモート デバッガー**)。
  
    リモート サーバーでリモート デバッガーを実行している場合は、リモート デバッガーのアプリを右クリックし、選択**管理者として実行**します。 場合を実行して、リモート サーバーではない、通常開始だけです。
  
2. リモート ツールを起動すると、最初に (またはそれを構成する前に)、**リモート デバッグの構成** ダイアログ ボックスが表示されます。  
  
    ![RemoteDebuggerConfWizardPage](../media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. Windows サービスの API が、(これは、Windows Server 2008 R2 でのみ発生します) もインストールされていない場合は、選択、**インストール**ボタンをクリックします。  
  
4. リモート ツールで利用される、使用するネットワークの種類を選択します。 少なくとも 1 つのネットワークの種類を選択する必要があります。 コンピューターがドメインを介して接続されている場合は、最初の項目を選択する必要があります。 コンピューターがワークグループまたはホーム グループを介して接続されている場合は、必要に応じて、2 番目または 3 番目の項目を選択する必要があります。  
  
5. 選択**のリモート デバッグ構成**ファイアウォールを構成し、ツールを起動します。  
  
6. 構成が完了すると、リモート デバッガーのウィンドウが表示されます。
  
    ![RemoteDebuggerWindow](../media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    接続のリモート デバッガーが待機しているようになりました。 サーバー名をメモしておき、後で Visual Studio で使用する構成と一致する必要がありますので、表示されている数値をポートします。  
  
   デバッグとリモート デバッガーを停止する必要が終了したら、クリックして**ファイル > 終了**ウィンドウ。 再起動することができます、**開始**メニューまたはコマンドラインから。  
  
   **\<リモート デバッガーのインストール ディレクトリ >\\< x86、x64、ARM、ARM64、または Appx > \msvsmon.exe**します。  
