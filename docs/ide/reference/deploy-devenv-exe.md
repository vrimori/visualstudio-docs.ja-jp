---
title: "/Deploy (devenv.exe) | Microsoft Docs"
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
  - "/deploy DEVENV スイッチ"
  - "deploy DEVENV スイッチ"
  - "配置 (アプリケーションを) [Visual Studio], ビルド後"
  - "Devenv, /deploy スイッチ"
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Deploy (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ビルドまたはリビルド後にソリューションを配置します。  マネージ コード プロジェクトでのみ使用できます。  
  
## 構文  
  
```  
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]  
```  
  
## 引数  
 `SolnConfigName`  
 必ず指定します。  `SolutionName` で指定したソリューションをビルドするために使用されるソリューション構成の名前です。  
  
 `SolutionName`  
 必ず指定します。  ソリューション ファイルの完全パスと名前です。  
  
 \/project  `ProjName`  
 省略可能です。  ソリューション内のプロジェクト ファイルのパスと名前です。  `SolutionName` フォルダーからプロジェクト ファイルまでの相対パス、プロジェクトの表示名、またはプロジェクト ファイルの完全パスと名前を入力できます。  
  
 \/projectconfig `ProjConfigName`  
 省略可能です。  `/project` 引数で指定されたプロジェクトをビルドするときに使用される、プロジェクトのビルド構成の名前です。  
  
## 解説  
 指定するプロジェクトは、配置プロジェクトである必要があります。  配置プロジェクト以外のプロジェクトを指定すると、ビルド済みのプロジェクトを配置するときにエラーが発生し、配置が失敗します。  
  
 空白を含む文字列は二重引用符で囲みます。  
  
 エラーなどのビルドの情報は、**\[コマンド\]** ウィンドウまたは `/out` スイッチで指定したログ ファイルに表示されます。  
  
## 使用例  
 次の例では、`MySolution` の `Release` ソリューション構成にある `Release` プロジェクト ビルド構成を使用し、`CSharpConsoleApp` プロジェクトを配置します。  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release   
```  
  
## 参照  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)   
 [\/Project](../../ide/reference/project-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)