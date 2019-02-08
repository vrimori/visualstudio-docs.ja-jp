---
title: リモート デバッガーのポートの割り当て |Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 05/18/2017
ms.topic: reference
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: feb5b247bb3e7bb8814946f5648408323a33084c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959749"
---
# <a name="remote-debugger-port-assignments"></a>リモート デバッガーのポートの割り当て
Visual Studio リモート デバッガーは、アプリケーションまたはバック グラウンド サービスとして実行できます。 アプリケーションとして実行される際には、次のように既定で割り当てられているポートを使用します。  

- Visual Studio 2019:4024

- Visual Studio 2017:4022

- Visual Studio 2015:4020  
  
- Visual Studio 2013:  
  
- Visual Studio 2012:4016  
  
  つまり、リモート デバッガーに割り当てられるポート番号はリリースごとに 2 つずつ増えます。 別の任意のポート番号を設定することができます。 ポート番号の設定方法は、後のセクションで説明します。  
  
## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>32 ビット オペレーティング システムのリモート デバッガーのポート  
 TCP 4022 (Visual Studio 2017 の場合) がメイン ポートであり、すべてのシナリオにこれが必要です。 これは、コマンド ラインまたはリモート デバッガー ウィンドウのいずれかから構成できます。  
  
 リモート デバッガー ウィンドウでは、**[ツール] > [オプション]** の順にクリックし、TCP/IP ポート番号を設定します。  
  
 コマンド ラインでは、**/port** スイッチを使用して「**msvsmon /port \<ポート番号>**」と入力して、リモート デバッガーを開始します。  
  
 リモート デバッグのヘルプに、リモート デバッガーのすべてのコマンド ライン スイッチが記載されています (リモート デバッガー ウィンドウで **F1** キーを押すか、または **[ヘルプ] > [使い方]** の順にクリックします)。  
  
## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>64 ビット オペレーティング システムのリモート デバッガーのポート  
 メインを使用して 64 ビット バージョンのリモート デバッガーが開始されると、既定のポート (4022)。  32 ビット プロセスをデバッグする場合、64 ビット バージョンのリモート デバッガーはポート 4023 でリモート デバッガーの 32 ビット バージョン (1 だけインクリメントした主なポート番号) を開始します。 32 ビットのリモート デバッガーを実行する場合は、4022 が使用され、4023 は使用されません。  
  
 このポートは、コマンドラインから構成できます。**Msvsmon/wow64port\<ポート番号 >** します。  
  
## <a name="the-discovery-port"></a>検出ポート  
 実行中のリモート デバッガーのインスタンスをネットワークで検出するには (たとえば、 **[プロセスにアタッチ]** ダイアログの **[検索]** ダイアログ)、UDP 3702 が使用されます。 これが使用されるのは、リモート デバッガーを実行しているコンピューターを検出する場合だけです。つまり、対象コンピューターのコンピューター名または IP アドレスが他の方法でわかれば省略できます。 これは検出用の標準ポートなので、ポート番号を構成することはできません。  
  
 探索を有効にしたくない場合は、検出を無効にコマンドラインから msvsmon を開始できます。**Msvsmon/nodiscovery**します。  
  
## <a name="remote-debugger-ports-on-azure"></a>Azure でのリモート デバッガーのポート  
 Azure のリモート デバッガーでは次のポートが使用されます。 クラウド サービス上のポートは、個々の VM 上のポートにマップされます。 すべてのポートは TCP です。  
  
|接続|クラウド サービス上のポート|VM 上のポート|
|-|-|-|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|  
  
## <a name="see-also"></a>関連項目
 [Remote Debugging](../debugger/remote-debugging.md)
