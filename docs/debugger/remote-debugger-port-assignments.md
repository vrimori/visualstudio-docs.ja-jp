---
title: "リモート デバッガーのポート割り当て |Microsoft ドキュメント"
ms.custom: H1Hack27Feb2017
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c541922ac18c28e085db37b6ac9fa9349adbeb9b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="remote-debugger-port-assignments"></a>リモート デバッガーのポートの割り当て
Visual Studio リモート デバッガーは、アプリケーションまたはバック グラウンド サービスとして実行できます。 アプリケーションとして実行される際には、次のように既定で割り当てられているポートを使用します。  

-   Visual Studio 2017: 4022

-   Visual Studio 2015: 4020  
  
-   Visual Studio 2013: 4018  
  
-   Visual Studio 2012: 4016  
  
 つまり、リモート デバッガーに割り当てられるポート番号はリリースごとに 2 つずつ増えます。 別の任意のポート番号を設定することができます。 ポート番号の設定方法は、後のセクションで説明します。  
  
## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>32 ビット オペレーティング システムのリモート デバッガーのポート  
 (Visual Studio 2017) の TCP 4022 メイン ポートのすべてのシナリオに必要です。 これは、コマンド ラインまたはリモート デバッガー ウィンドウのいずれかから構成できます。  
  
 リモート デバッガー] ウィンドウで、[**ツール > オプション**、TCP/IP ポート番号を設定します。  
  
 コマンド ライン上でリモート デバッガーを起動、**ポート**スイッチ: **msvsmon/port\<ポート番号 >**です。  
  
 リモート デバッグのヘルプで、すべてのリモート デバッガーのコマンド ライン スイッチを見つけることができます (キーを押して**F1**  をクリックして**ヘルプ > 使用状況**リモート デバッガー ウィンドウで)。  
  
## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>64 ビット オペレーティング システムのリモート デバッガーのポート  
 64 ビット バージョンのリモート デバッガーが開始されたときに、既定では 4022 ポートを使用します。  32 ビット プロセスをデバッグする場合、64 ビット バージョンのリモート デバッガーは、ポート 4023 でリモート デバッガーの 32 ビット バージョンを開始します。 32 ビットのリモート デバッガーを実行する場合は、4022 を使用してし、4023 は使用されません。  
  
 このポートは、コマンドラインから構成できます: **Msvsmon/wow64port\<ポート番号 >**です。  
  
## <a name="the-discovery-port"></a>検出ポート  
 実行中のリモート デバッガーのインスタンスをネットワークで検出するには (たとえば、 **[プロセスにアタッチ]** ダイアログの **[検索]** ダイアログ)、UDP 3702 が使用されます。 これが使用されるのは、リモート デバッガーを実行しているコンピューターを検出する場合だけです。つまり、対象コンピューターのコンピューター名または IP アドレスが他の方法でわかれば省略できます。 これは検出用の標準ポートなので、ポート番号を構成することはできません。  
  
 検出を有効にしない場合は、コマンド ラインから検出を無効にして msvsmon を開始できます。次のように入力します。  **Msvsmon /nodiscovery**  
  
## <a name="remote-debugger-ports-on-azure"></a>Azure でのリモート デバッガーのポート  
 Azure のリモート デバッガーでは次のポートが使用されます。 クラウド サービス上のポートは、個々の VM 上のポートにマップされます。 すべてのポートは TCP です。  
  
||||  
|-|-|-|  
|**接続**|**クラウド サービス上のポート**|**VM 上のポート**|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|  
  
## <a name="see-also"></a>参照  
 [Remote Debugging](../debugger/remote-debugging.md)