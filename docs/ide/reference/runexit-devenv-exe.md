---
title: "/Runexit (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/runexit Devenv スイッチ"
  - "Devenv, /runexit スイッチ"
  - "runexit Devenv スイッチ"
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Runexit (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定したプロジェクトまたはソリューションをコンパイルおよび実行してから、統合開発環境 \(IDE: Integrated Development Environment\) を閉じます。  
  
## 構文  
  
```  
devenv /runexit {SolutionName|ProjectName}  
```  
  
## 引数  
 `SolutionName`  
 必ず指定します。  ソリューション ファイルの完全パスおよび名前です。  
  
 `ProjectName`  
 必ず指定します。  プロジェクト ファイルの完全パスおよび名前です。  
  
## 解説  
 アクティブなソリューション構成に対して指定された設定に従ってプロジェクトまたはソリューションをコンパイルして実行します。  このスイッチは、IDE を最小化した状態でプロジェクトまたはソリューションを実行し、実行が完了したら IDE を終了します。  
  
-   空白を含む文字列は二重引用符で囲みます。  
  
-   エラーなどの情報は、**\[コマンド\]** ウィンドウまたは `/out` スイッチで指定した任意のログ ファイルに表示されます。  
  
## 使用例  
 次のコードでは、アクティブな配置構成を使用し、IDE を最小化した状態で `MySolution` ソリューションを実行してから IDE を終了します。  
  
```  
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## 参照  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)   
 [\/Run](../../ide/reference/run-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)