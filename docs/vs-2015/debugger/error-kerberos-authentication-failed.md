---
title: 'エラー: Kerberos 認証に失敗しました |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.callback_kerberos_auth_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c18053f9-9074-4bc3-a8bf-13e4acbea921
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ec03ae3d3b64435877b51996cb84a1768cc4a42
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732343"
---
# <a name="error-kerberos-authentication-failed"></a>エラー : Kerberos 認証に失敗しました。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

リモート デバッグを実行するときに、次のエラー メッセージが表示されることがあります。  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos auythentication failed.  
```  
  
 このエラーは、Visual Studio リモート デバッグ モニターがローカル システム アカウントまたはネットワーク サービス アカウントで実行されている場合に発生します。 これらのアカウントでは、リモート デバッガーが Visual Studio デバッガー ホスト コンピューターに接続するときに Kerberos 認証接続を確立する必要があります。  
  
 Kerberos 認証は、以下の場合には使用できません。  
  
- ターゲット コンピューターまたはデバッガー ホスト コンピューターがドメインではなくワークグループに属している。  
  
   \- または -  
  
- ドメイン コントローラーで Kerberos が無効になっている。  
  
  Kerberos 認証が使用できない場合は、Visual Studio リモート デバッグ モニターの実行に使用するアカウントを変更してください。 手順については、次を参照してください。[エラー: ターゲット コンピューターで、Visual Studio リモート デバッガー サービスは、このコンピューターに接続できない](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)します。  
  
  両方のコンピューターが同じドメインに接続しているにもかかわらず、このメッセージが表示される場合は、ターゲット コンピューターの DNS がデバッガー ホスト コンピューターの名前を正しく解決していることを確認してください。 以降の手順を参照してください。  
  
### <a name="to-verify-that-dns-on-the-target-computer-is-correctly-resolving-the-debugger-host-computer-name"></a>ターゲット コンピューターの DNS がデバッガー ホスト コンピューター名を正しく解決していることを確認するには  
  
1.  ターゲット コンピューターで開く、**開始**メニューで、**アクセサリ**順にクリックします**コマンド プロンプト**。  
  
2.  **コマンド プロンプト**ウィンドウで、種類。  
  
    ```  
    ping <debugger_host_computer_name>  
    ```  
  
3.  `ping` の応答の 1 行目には、DNS が返した完全なコンピューター名と IP アドレスが表示されます。  
  
4.  デバッガー ホスト コンピューターでは、開く、**コマンド プロンプト**ウィンドウと実行`ipconfig`します。  
  
5.  IP アドレス値を比較します。  
  
## <a name="see-also"></a>関連項目  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)



