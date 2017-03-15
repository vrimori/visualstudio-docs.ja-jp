---
title: "64 ビット アプリケーションをデバッグする | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "デバッグ [Visual Studio]、64 ビット"
  - "64 ビット デバッグ"
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 64 ビット アプリケーションをデバッグする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ローカル コンピューターまたはリモート コンピューターで実行されている 64 ビット アプリケーションをデバッグできます。  
  
 リモート コンピューターで実行されている 64 ビット アプリケーションをデバッグするには、「[リモート デバッグ](../debugger/remote-debugging.md)」をご覧ください。  
  
 ローカルで 64 ビット アプリケーションをデバッグする場合、Visual Studio では 64 ビット ワーカー プロセス \(msvsmon.exe\) を使用して、32 ビットの Visual Studio プロセス内で実行できない低水準の操作を実行します。  
  
 .NET Framework version 3.5 以前を使用する 64 ビット プロセスでは、混合モードのデバッグはサポートされません。  
  
## 64 ビット アプリケーションのデバッグ  
 64 ビット アプリケーションのデバッグを実行するには次のことを行います。  
  
1.  C\# コンソール アプリケーションなど、Visual Studio ソリューションを作成します。  
  
2.  構成マネージャーを使用して、構成を 64 ビットに設定します。 詳細については、「[方法 : プロジェクトを構成して対象プラットフォームを設定する](../ide/how-to-configure-projects-to-target-platforms.md)」を参照してください。  
  
3.  この時点で、64 ビット バージョンのリモート デバッガー \(msvsmon.exe\) が起動します。 64 ビット構成のソリューションが開いている限り、これが実行されます。  
  
4.  デバッグを開始します。 操作は 32 ビット構成と変わりません。 エラーが発生した場合は、以下のトラブルシューティング セクションをご覧ください。  
  
## トラブルシューティング \(64 ビット デバッグ\)  
 "64 ビット デバッグ操作に予想以上に時間がかかっています" というエラーが表示されることがあります。 この場合、Visual Studio は 64 ビット バージョンの msvsmon.exe に要求を送信し、その要求の結果が返されるまでに長い時間がかかっています。  
  
 このエラーの主な原因として次の 2 つがあります。  
  
-   ネットワーク スタックの信頼性を低下させるネットワーク セキュリティ ソフトウェアがコンピューターにインストールされており、localhost に向かうパケットがドロップされています。 すべてのネットワーク セキュリティ ソフトウェアを無効にしてみて、問題が解決するか確認します。 解決した場合は、ネットワーク セキュリティ ソフトウェア ベンダーに、ソフトウェアが localhost トラフィックに干渉していることを報告します。  
  
-   Visual Studio でハングまたはパフォーマンスに関する問題が発生しています。 問題が定期的に発生する場合は、Visual Studio \(devenv.exe\) とワーカー プロセス \(msvsmon.exe\) のダンプを収集して、Microsoft に送信できます。 問題の報告については、「[Visual Studio で問題を報告する方法](../Topic/How%20to%20Report%20a%20Problem%20with%20Visual%20Studio.md)」をご覧ください。  
  
## 参照  
 [64 ビット アプリケーション](../Topic/64-bit%20Applications.md)   
 [64 ビット用プログラムの構成](/visual-cpp/build/configuring-programs-for-64-bit-visual-cpp)   
 [Visual Studio IDE の 64 ビット サポート](../ide/visual-studio-ide-64-bit-support.md)   
 [ダンプ ファイルを使用したアプリのクラッシュとハングのデバッグ](../debugger/using-dump-files.md)   
 [リモート デバッグ](../debugger/remote-debugging.md)