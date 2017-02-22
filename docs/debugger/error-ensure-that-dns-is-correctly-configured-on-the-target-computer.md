---
title: "エラー : 対象コンピューターで DNS が正しく構成されていることを確認してください。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.callback_dns_failed"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 2d364caf-73af-4186-bf9b-af186331cbe8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# エラー : 対象コンピューターで DNS が正しく構成されていることを確認してください。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

リモート デバッグを行おうとすると、次のエラー メッセージが表示される場合があります。  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 このエラーは、対象コンピューターが Visual Studio デバッガー ホスト コンピューターの名前を解決できない場合に発生します。  ターゲット コンピューターの DNS 設定を確認します。  
  
-   Windows 8.1、Vista、Windows 7、Windows Server 2012、Windows Server 2008、または Windows Server 2008 R2 で DNS 設定を表示する方法については、 **\[スタート\]** メニューの **\[ヘルプとサポート\]** をクリックし、「TCP\/IP 設定の変更」を検索してください。  
  
-   詳細については、[Microsoft Windows Web サイト](http://go.microsoft.com/fwlink/?LinkId=252720) にアクセスし、「TCP\/IP 設定の変更」を検索してください。  
  
 DNS に関する問題を解決できない場合は、別のコンピューターでリモート デバッガーを実行してみてください。  このエラーは、リモート デバッガーをローカル システム アカウントまたはネットワーク サービス アカウントで実行した場合のみ発生します。  リモート デバッガーを別のアカウントで実行する場合は、DNS を必要としない NTLM 認証を使用できます。  からドラッグします。  手順については、「[エラー : 対象コンピューター上の Visual Studio リモート デバッガーが、このコンピューターに接続できません。](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)」を参照してください。