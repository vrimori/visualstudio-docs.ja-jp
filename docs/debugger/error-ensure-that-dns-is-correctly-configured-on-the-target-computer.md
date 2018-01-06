---
title: "エラー: は、DNS は、ターゲット コンピューターに正しく構成されていることを確認してください |。Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.callback_dns_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a349dc3a1e2368b4e1772d4bf717483d5bc2dc5d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>エラー : 対象コンピューターで DNS が正しく構成されていることを確認してください。
リモート デバッグを行おうとすると、次のエラー メッセージが表示される場合があります。  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 このエラーは、対象コンピューターが Visual Studio デバッガー ホスト コンピューターの名前を解決できない場合に発生します。 ターゲット コンピューターの DNS 設定を確認します。  
  
-   Windows 8.1、Vista、Windows 7、Windows Server 2012、Windows Server 2008、または Windows Server 2008 R2 で DNS 設定を表示する方法については、これを行う: に、**開始**] メニューの [選択**ヘルプし、サポート**、しの検索**TCP/IP 設定を変更**です。  
  
-   詳細についてを参照してください[Microsoft Windows web サイト](http://go.microsoft.com/fwlink/?LinkId=252720)を検索および**TCP/IP 設定を変更**です。  
  
 DNS に関する問題を解決できない場合は、別のコンピューターでリモート デバッガーを実行してみてください。 このエラーは、リモート デバッガーをローカル システム アカウントまたはネットワーク サービス アカウントで実行した場合のみ発生します。 リモート デバッガーを別のアカウントで実行する場合は、DNS を必要としない NTLM 認証を使用できます。 である必要があります。 手順については、次を参照してください。[エラー: 対象のコンピューター上の Visual Studio リモート デバッガー サービスは、このコンピューターに接続できません](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)です。