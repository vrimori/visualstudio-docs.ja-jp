---
title: "/Project (devenv.exe) | Microsoft Docs"
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
  - "/project DEVENV スイッチ"
  - "配置プロジェクト, 指定"
  - "Devenv, /project スイッチ"
  - "project Devenv スイッチ (/project)"
  - "プロジェクト [Visual Studio], ビルド"
  - "プロジェクト [Visual Studio], 消去"
  - "プロジェクト [Visual Studio], 再度ビルド"
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Project (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定したソリューション構成にある単一のプロジェクトを、ビルド、クリーン、リビルド、または配置対象として指定します。  
  
## 構文  
  
```  
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName   
[/project ProjName] [/projectconfig ProjConfigName]   
```  
  
## 引数  
 \/build  
 `/project`  `ProjName` で指定したプロジェクトをビルドします。  
  
 \/clean  
 ビルド時に作成された中間ファイルと出力ディレクトリを消去します。  
  
 \/rebuild  
 `/project`  `ProjName` で指定したプロジェクトを消去してからビルドします。  
  
 \/deploy  
 ビルドまたはリビルドの後でプロジェクトが配置されるのを指定します。  
  
 `SolnConfigName`  
 必ず指定します。  `SolutionName` で指定したソリューションに適用される、ソリューション構成の名前です。  
  
 `SolutionName`  
 必ず指定します。  ソリューション ファイルの完全パスと名前です。  
  
 \/project `ProjName`  
 省略可能です。  ソリューション内のプロジェクト ファイルのパスと名前です。  `SolutionName` フォルダーからプロジェクト ファイルまでの相対パス、プロジェクトの表示名、またはプロジェクト ファイルの完全パスと名前を入力できます。  
  
 \/projectconfig `ProjConfigName`  
 省略可能です。  `/project` 引数で指定したプロジェクトに適用される、プロジェクトのビルド構成の名前です。  
  
## 解説  
  
-   `devenv /build` コマンド、\/`clean` コマンド、`/rebuild` コマンドまたは `/deploy` コマンドに含めて使用する必要があります。  
  
-   空白を含む文字列は二重引用符で囲みます。  
  
-   エラーなどのビルドの情報は、**\[コマンド\]** ウィンドウまたは `/out` スイッチで指定したログ ファイルに表示されます。  
  
## 使用例  
 この例では、`MySolution` の `Debug` ソリューション構成にある `Debug` プロジェクト ビルド構成を使用し、`CSharpConsoleApp` プロジェクトをビルドします。  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## 参照  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)   
 [\/ProjectConfig](../../ide/reference/projectconfig-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Deploy](../../ide/reference/deploy-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)