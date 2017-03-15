---
title: "セキュリティ警告: 信頼されていないユーザーが所有するプロセスにアタッチするには危険が伴います。以下の情報に関して疑わしい点がある場合や、不明な場合は、このプロセスにアタッチしないでください。 | Microsoft Docs"
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
  - "vs.debug.attachsecuritywarning"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# セキュリティ警告: 信頼されていないユーザーが所有するプロセスにアタッチするには危険が伴います。以下の情報に関して疑わしい点がある場合や、不明な場合は、このプロセスにアタッチしないでください。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この警告ダイアログ ボックスは、部分的に信頼されているコードを含むプロセスや、信頼関係のないユーザーが所有するプロセスにアタッチしようとすると表示されます。  悪意のあるコードを含む信頼関係のないプロセスによって、デバッグを実行しているコンピューターに障害が発生する可能性があります。  何らかの理由によりプロセスを信頼していない場合は、**\[キャンセル\]** をクリックしてデバッグを回避します。  
  
 正当なシナリオのデバッグ時にこの警告を表示しないようにするには、Visual Studio を閉じて、レジストリ キー `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning` の値を 1 に設定し、Visual Studio を再起動します。  シナリオのデバッグが終わったら、値を 0 にリセットし、Visual Studio を再起動します。  
  
 "信頼できるユーザー" には、ユーザー自身と、.NET Framework がインストールされているコンピューターで一般に定義される標準ユーザーのグループ \(`aspnet`、`localsystem`、`networkservice`、`localservice` など\) が含まれます。  
  
## UIElement の一覧  
 \[名前\]  
 デバッグが要求されたアセンブリの名前  
  
 User  
 現在のユーザー  
  
 \[アタッチ\]  
 クリックすると、アタッチしてデバッグを継続します。  
  
 \[アタッチしない\]  
 プロセスにアタッチしません。  
  
## 参照  
 [実行中のプロセスへのアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)