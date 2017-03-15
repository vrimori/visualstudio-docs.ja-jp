---
title: "/Rebuild (devenv.exe) | Microsoft Docs"
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
  - "/rebuild Devenv スイッチ"
  - "アプリケーション [Visual Studio], 再度ビルド"
  - "Devenv, /rebuild スイッチ"
  - "プロジェクト [Visual Studio], 再度ビルド"
  - "rebuild Devenv スイッチ (/rebuild)"
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Rebuild (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定したソリューション構成を消去してからビルドします。  
  
## 構文  
  
```  
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]  
```  
  
## 引数  
 `SolnConfigName`  
 必須。  `SolutionName` で指定したソリューションをリビルドするために使用されるソリューション構成の名前です。  
  
 `SolutionName`  
 必須。  ソリューション ファイルの完全パスと名前です。  
  
 \/project  `ProjName`  
 省略可能。  ソリューション内のプロジェクト ファイルのパスと名前です。  `SolutionName` フォルダーからプロジェクト ファイルまでの相対パス、プロジェクトの表示名、またはプロジェクト ファイルの完全パスと名前を入力できます。  
  
 \/projectconfig `ProjConfigName`  
 省略可能。  引数 `/project` で指定されたプロジェクトをリビルドするときに使用される、プロジェクトのビルド構成の名前です。  
  
## 解説  
  
-   このスイッチは、統合開発環境 \(IDE: Integrated Development Environment\) の **\[ソリューションのリビルド\]** メニュー コマンドと同じ機能を果たします。  
  
-   空白を含む文字列は二重引用符で囲みます。  
  
-   エラーなどの削除とビルドの情報は、**\[コマンド\]** ウィンドウまたは `/out` スイッチで指定したログ ファイルに表示されます。  
  
## 使用例  
 次の例では、`MySolution` の `Debug` ソリューション構成にある `Debug` プロジェクト ビルド構成を使用し、`CSharpWinApp` プロジェクトを削除し、リビルドします。  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## 参照  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)