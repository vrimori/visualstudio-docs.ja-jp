---
title: "Mark | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Mark
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe の **Mark** オプションは、プロファイル データ ファイルに指定した情報を挿入します。  マークは個別の VSPerfReport レポートまたはプロファイラー UI のマーク レポート ビューに一覧表示できます。  **Mark** を使用して、レポートおよびビュー フィルターの開始点または終了点を指定できます。  
  
 コマンド ラインで指定するオプションは **Mark** のみにする必要があります。  
  
## 構文  
  
```  
VSPerfCmd.exe /Mark:MarkID,[MarkName]   
```  
  
#### パラメーター  
 `MarkID`  
 プロファイラー ビューおよびレポートにマーク ID として一覧表示される、ユーザー定義の整数です。  `MarkID` は一意である必要はありません。  
  
 `MarkName`  
 \(オプション\) プロファイラー ビューおよびレポートにマーク名として一覧表示される、ユーザー定義の文字列です。  `MarkName` が指定されない場合、マーク一覧の "マーク名" フィールドは空になります。  スペースやスラッシュ \("\/"\) を含む文字列は引用符で囲みます。  
  
## 使用例  
 この例では、ID が 123、名前が "TestMark" というマークを挿入します。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## 参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)