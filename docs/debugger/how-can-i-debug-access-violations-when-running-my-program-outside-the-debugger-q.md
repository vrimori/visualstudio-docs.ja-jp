---
title: "プログラムの実行中にデバッガーの外部で発生するアクセス違反をデバッグするには | Microsoft Docs"
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
  - "vs.debug.access"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "アクセス違反デバッグ"
  - "デバッグ [Visual Studio], アクセス違反"
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# プログラムの実行中にデバッガーの外部で発生するアクセス違反をデバッグするには
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## 問題の説明  
 プログラムが Visual Studio 環境では正しく動作するのに、Windows オペレーティング システムでスタンドアロンで実行するとアクセス違反が発生します。  どのようにデバッグしたらいいのでしょうか。  
  
## ソリューション  
 [&#91;Just\-In\-Time デバッグ&#93;](../debugger/just-in-time-debugging-in-visual-studio.md) オプションを設定し、アクセス違反が発生するまでプログラムをスタンドアロンで実行します。  その後、\[アクセス違反\] ダイアログ ボックスが表示されたら、\[キャンセル\] をクリックしてデバッガーを起動します。  
  
 サポート技術情報の文書「How to Locate Where a General Protection \(GP\) Fault Occurs \(Q133174\)」も参照してください。サポート技術情報の文書は、MSDN ライブラリ CD\-ROM または「 [http:\/\/support.microsoft.com\/](http://support.microsoft.com/)」で参照できます。  
  
## 参照  
 [ネイティブ コードのデバッグに関する FAQ](../debugger/debugging-native-code-faqs.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)