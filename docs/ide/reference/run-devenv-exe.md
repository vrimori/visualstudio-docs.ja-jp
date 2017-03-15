---
title: "/Run (devenv.exe) | Microsoft Docs"
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
  - "/r Devenv スイッチ"
  - "/run Devenv"
  - "アプリケーション [Visual Studio], 実行"
  - "Devenv, /run スイッチ"
  - "r Devenv スイッチ (/r)"
  - "run Devenv スイッチ"
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Run (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定したプロジェクトまたはソリューションをコンパイルし、実行します。  
  
## 構文  
  
```  
devenv {/run|/r} {SolutionName|ProjectName}  
```  
  
## 引数  
 `SolutionName`  
 必ず指定します。  ソリューション ファイルの完全パスおよび名前です。  
  
 `ProjectName`  
 必ず指定します。  プロジェクト ファイルの完全パスおよび名前です。  
  
## 解説  
 アクティブなソリューション構成に対して指定された設定に従ってプロジェクトまたはソリューションをコンパイルして実行します。  このスイッチは、統合開発環境 \(IDE: Integrated Development Environment\) を起動し、プロジェクトまたはソリューションの実行が完了しても IDE をアクティブな状態のままにします。  
  
-   空白を含む文字列は二重引用符で囲みます。  
  
-   エラーなどの情報は、**\[コマンド\]** ウィンドウまたは `/out` スイッチで指定した任意のログ ファイルに表示されます。  
  
## 使用例  
 アクティブな配置構成を使用して `MySolution` を実行するコードは次のとおりです。  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## 参照  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)   
 [\/Runexit](../../ide/reference/runexit-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)