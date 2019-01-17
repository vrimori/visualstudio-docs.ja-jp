---
title: エラー :DNS では、ターゲット コンピューターに正しく構成されているがあることを確認します |。Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b884326eb2e3aeeb03381088d0dc5b7caa07475
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53923060"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>エラー :対象コンピューターで DNS が正しく構成されていることを確認してください
リモート デバッグを行おうとすると、次のエラー メッセージが表示される場合があります。  
  
```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 このエラーは、対象コンピューターが Visual Studio デバッガー ホスト コンピューターの名前を解決できない場合に発生します。 ターゲット コンピューターの DNS 設定を確認します。  
  
- Windows 8.1、Vista、Windows 7、Windows Server 2012、Windows Server 2008、または Windows Server 2008 R2 で DNS 設定を表示する方法については、**[スタート]** メニューの **[ヘルプとサポート]** を選択し、「**TCP/IP 設定の変更**」を検索してください。  
  
- 詳細については、[Microsoft Windows Web サイト](http://go.microsoft.com/fwlink/?LinkId=252720)にアクセスし、「**TCP/IP 設定の変更**」を検索してください。  
  
  DNS に関する問題を解決できない場合は、別のコンピューターでリモート デバッガーを実行してみてください。 このエラーは、リモート デバッガーをローカル システム アカウントまたはネットワーク サービス アカウントで実行した場合のみ発生します。 リモート デバッガーを別のアカウントで実行する場合は、DNS を必要としない NTLM 認証を使用できます。 . 手順については、次を参照してください。[エラー。対象コンピューター上の Visual Studio リモート デバッガーが、このコンピューターに接続できません](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)
