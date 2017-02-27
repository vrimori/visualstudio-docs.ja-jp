---
title: "開始 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 開始
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Start** オプションは、プロファイラーを指定したプロファイル方法に初期化する VSPerfCmd.exe のオプションです。  
  
## 構文  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### パラメーター  
 `Method`  
 次のいずれかのキーワードを指定する必要があります。  
  
-   **TRACE** \- インストルメンテーション メソッドを指定します。  
  
-   **SAMPLE** \- サンプリング メソッドを指定します。  
  
-   **COVERAGE** \- コード カバレッジを指定します。  
  
-   **CONCURRENCY** \-リソース競合メソッドを指定します。  
  
## 必須のオプション  
 **Start** をコマンド ラインで指定する場合は、**Output** オプションを指定する必要があります。  
  
 **Output:** `filename`  
 出力ファイル名を指定します。  
  
## 排他的オプション  
 次のオプションは、コマンド ラインで **Start** オプションを使用する場合にのみ使用できます。  
  
 **CrossSession**&#124;**CS**  
 プロセス間プロファイリングを有効にします。  オプション名 **CrossSession** と **CS** は、両方ともサポートされます。  
  
 **User:**\[`domain\`\]`username`  
 指定したアカウントからモニターへのクライアント アクセスを有効にします。  
  
 **WinCounter:** `Path` \[**Automark**:`n`\]  
 **WinCounter** プロファイル データ ファイルにマークとして含まれる Windows パフォーマンス カウンターを指定します。  **AutoMark** は、データ ファイルの収集間隔をミリ秒単位で指定します。  
  
## 無効なオプション  
 次のオプションは、コマンド ラインで **Start** オプションと共に使用できません。  
  
 **Status**  
 **Status** は、プロファイリングされるプロセスに適用されます。  プロセスとスレッド、およびそれらの現在のプロファイル状態 \(オン\/オフ\) が表示されます。  たとえば、プロセスが停止された場合、**Status** はこれをレポートに表示しません。  **Status** はプロセスがプロファイリングされるかどうかを示します。  
  
 **Shutdown**\[**:**`Timeout`\]  
 プロファイラーをオフにします。  
  
## 使用例  
 VSPerfCmd.exe の **Start** オプションを使用して、プロファイラーを初期化する方法を次の例に示します。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## 参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)