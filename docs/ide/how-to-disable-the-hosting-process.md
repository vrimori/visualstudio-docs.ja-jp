---
title: "方法 : ホスト プロセスを無効にする | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ホスト プロセス, 無効化"
  - "vshost.exe, 無効化 (ホスト プロセスを)"
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 方法 : ホスト プロセスを無効にする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ホスト プロセスが有効になっていると、特定の API の呼び出しに影響する場合があります。  影響がある場合は、正しい結果が返るようにホスト プロセスを無効にする必要があります。  
  
### ホスト プロセスを無効にするには  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で、実行可能なプロジェクトを開きます。  実行可能ファイルを生成しないプロジェクト \(クラス ライブラリやサービス プロジェクトなど\) には、このオプションがありません。  
  
2.  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
3.  **\[デバッグ\]** タブをクリックします。  
  
4.  **\[Visual Studio ホスティング プロセスを有効にする\]** チェック ボックスをオフにします。  
  
 ホスト プロセスが無効になると、一部のデバッグ機能が使用できなくなったり、パフォーマンスが低下したりします。  詳細については、「[プロセスのデバッグとホスト](../debugger/debugging-and-the-hosting-process.md)」を参照してください。  
  
 一般的に、ホスト プロセスが無効になると、次のことが起こります。  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] アプリケーションのデバッグが始まるまでの時間が長くなる。  
  
-   デザイン時の式評価が使用できなくなる。  
  
-   部分信頼デバッグが使用できなくなる。  
  
## 参照  
 [プロセスのデバッグとホスト](../debugger/debugging-and-the-hosting-process.md)   
 [ホスト プロセス \(vshost.exe\)](../ide/hosting-process-vshost-exe.md)   
 [Builds During Application Development](http://msdn.microsoft.com/ja-jp/c9497d62-3b7b-4449-88e8-cf27acc9efe6)