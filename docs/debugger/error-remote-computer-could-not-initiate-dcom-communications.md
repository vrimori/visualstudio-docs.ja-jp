---
title: "エラー : リモート コンピューターは DCOM 通信を初期化できませんでした。 | Microsoft Docs"
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
  - "vs.debug.error.unmarshal_callback_failed"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: bbba0766-2502-4ef1-a75d-bf1f0db39e37
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# エラー : リモート コンピューターは DCOM 通信を初期化できませんでした。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

リモート コンピューターがローカル コンピューターと通信しようとしたときに DCOM エラーが発生しました。  ローカル コンピューターは、  
  
 Visual Studio を実行しているコンピューターです。  このエラーが発生する原因は複数あります。  
  
-   ローカル マシンのファイアウォールが有効になっていない。  
  
-   リモート マシンからローカル マシンへの Windows 認証が機能していない。  
  
### このエラーを解決するには  
  
1.  ローカル コンピューターで Windows ファイアウォールが有効になっている場合は、「[デバイスのリモート ツールのセットアップ](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)」を参照し、ローカル デバッグができるようにファイアウォールを設定する手順を確認してください。  
  
2.  リモート サーバーからローカル コンピューターのファイル共有を開いてみて Windows 認証をテストします。  
  
3.  Windows 認証を復元するために、両方のコンピューターを再起動してみます。  Kerberos エラーがないかどうかローカル コンピューターとリモート コンピューターのイベント ログを確認し、既知の問題がないかどうかドメイン管理者に問い合わせてください。  
  
## 参照  
 [デバイスのリモート ツールのセットアップ](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)