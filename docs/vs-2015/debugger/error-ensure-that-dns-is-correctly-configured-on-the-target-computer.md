---
title: 'エラー: は、DNS では、ターゲット コンピューターに正しく構成されているがあることを確認します |。Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2d364caf-73af-4186-bf9b-af186331cbe8
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f0be44e07a42b132f00b476aa7cf4148720933a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536876"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>エラー : 対象コンピューターで DNS が正しく構成されていることを確認してください。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[エラー: DNS がターゲット コンピューターに正しく構成されていることを確認](https://docs.microsoft.com/visualstudio/debugger/error-ensure-that-dns-is-correctly-configured-on-the-target-computer)します。  
  
リモート デバッグを行おうとすると、次のエラー メッセージが表示される場合があります。  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 このエラーは、対象コンピューターが Visual Studio デバッガー ホスト コンピューターの名前を解決できない場合に発生します。 ターゲット コンピューターの DNS 設定を確認します。  
  
-   Windows 8.1、Vista、Windows 7、Windows Server 2012、Windows Server 2008、または Windows Server 2008 R2 で DNS 設定を表示する方法については、これを行う: で、**開始**] メニューの [選択**ヘルプし、サポート**を検索し**TCP/IP 設定の変更**します。  
  
-   詳細についてを参照してください[Microsoft Windows web サイト](http://go.microsoft.com/fwlink/?LinkId=252720)検索**TCP/IP 設定の変更**します。  
  
 DNS に関する問題を解決できない場合は、別のコンピューターでリモート デバッガーを実行してみてください。 このエラーは、リモート デバッガーをローカル システム アカウントまたはネットワーク サービス アカウントで実行した場合のみ発生します。 リモート デバッガーを別のアカウントで実行する場合は、DNS を必要としない NTLM 認証を使用できます。 . 手順については、次を参照してください。[エラー: ターゲット コンピューターで、Visual Studio リモート デバッガー サービスは、このコンピューターに接続できない](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)します。



