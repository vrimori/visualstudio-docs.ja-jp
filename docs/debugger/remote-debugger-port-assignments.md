---
title: リモート デバッガーのポートの割り当て |Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: reference
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1570468a56a4eaba80965d8feea669a0d3f3cb1c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905065"
---
# <a name="remote-debugger-port-assignments"></a>リモート デバッガーのポートの割り当て
Visual Studio リモート デバッガーは、アプリケーションまたはバック グラウンド サービスとして実行できます。 アプリケーションとして実行される際には、次のように既定で割り当てられているポートを使用します。  

- Visual Studio 2017: 4022

- Visual Studio 2015: 4020  
  
- Visual Studio 2013: 4018  
  
- Visual Studio 2012: 4016  
  
  つまり、リモート デバッガーに割り当てられるポート番号はリリースごとに 2 つずつ増えます。 別の任意のポート番号を設定することができます。 ポート番号の設定方法は、後のセクションで説明します。  
  
## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>32 ビット オペレーティング システムのリモート デバッガーのポート  
 TCP 4022 (Visual Studio 2017) では、メインのポートとのすべてのシナリオが必要です。 これは、コマンド ラインまたはリモート デバッガー ウィンドウのいずれかから構成できます。  
  
 リモート デバッガー] ウィンドウで、[**ツール > オプション**、TCP/IP ポート番号を設定します。  
  
 使用してリモート デバッガーを開始、コマンドラインで、 **/port**スイッチ: **msvsmon/port\<ポート番号 >** します。  
  
 リモート デバッグのヘルプで、すべてのリモート デバッガー コマンド ライン スイッチを見つけることができます (キーを押して**F1**  をクリックしてまたは**ヘルプ > 使用状況**リモート デバッガー ウィンドウで)。  
  
## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>64 ビット オペレーティング システムのリモート デバッガーのポート  
 64 ビット バージョンのリモート デバッガーが開始されると、既定でポート 4022 を使用します。  32 ビット プロセスをデバッグする場合、64 ビット バージョンのリモート デバッガーは、ポート 4023 でリモート デバッガーの 32 ビット バージョンを開始します。 32 ビットのリモート デバッガーを実行する場合は、使用 4022 を使用して、4023 は使用されません。  
  
 このポートは、コマンドラインから構成できます: **Msvsmon/wow64port\<ポート番号 >** します。  
  
## <a name="the-discovery-port"></a>検出ポート  
 実行中のリモート デバッガーのインスタンスをネットワークで検出するには (たとえば、 **[プロセスにアタッチ]** ダイアログの **[検索]** ダイアログ)、UDP 3702 が使用されます。 これが使用されるのは、リモート デバッガーを実行しているコンピューターを検出する場合だけです。つまり、対象コンピューターのコンピューター名または IP アドレスが他の方法でわかれば省略できます。 これは検出用の標準ポートなので、ポート番号を構成することはできません。  
  
 検出を有効にしない場合は、コマンド ラインから検出を無効にして msvsmon を開始できます。次のように入力します。  **Msvsmon /nodiscovery**  
  
## <a name="remote-debugger-ports-on-azure"></a>Azure でのリモート デバッガーのポート  
 Azure のリモート デバッガーでは次のポートが使用されます。 クラウド サービス上のポートは、個々の VM 上のポートにマップされます。 すべてのポートは TCP です。  
  
|接続|クラウド サービス上のポート|VM 上のポート|
|-|-|-|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|  
  
## <a name="see-also"></a>関連項目  
 [Remote Debugging](../debugger/remote-debugging.md)