---
title: "/Clean (devenv.exe) | Microsoft Docs"
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
  - "/clean Devenv スイッチ"
  - "ビルド [Team System], 消去 (ファイルを)"
  - "clean Devenv スイッチ"
  - "Devenv, /clean スイッチ"
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Clean (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

中間ファイルと出力ディレクトリをすべて消去します。  
  
## 構文  
  
```  
devenv FileName /Clean [ /project projectnameorfile [/projectconfig name ] ]  
```  
  
## 引数  
 `FileName`  
 必ず指定します。  ソリューション ファイルまたはプロジェクト ファイルの完全なパスと名前です。  
  
 \/project  `ProjName`  
 省略可能です。  ソリューション内のプロジェクト ファイルのパスと名前です。  `SolutionName` フォルダーからプロジェクト ファイルまでの相対パス、プロジェクトの表示名、またはプロジェクト ファイルの完全パスと名前を入力できます。  
  
 \/projectconfig `ProjConfigName`  
 省略可能です。  `/project` 引数で指定されたプロジェクトを消去するときに使用される、プロジェクトのビルド構成の名前です。  
  
## 解説  
 このスイッチは、統合開発環境 \(IDE: Integrated Development Environment\) の **\[ソリューションのクリーン\]** メニュー コマンドと同じ機能を果たします。  
  
 空白を含む文字列は二重引用符で囲みます。  
  
 エラーなどの削除とビルドの情報は、**\[コマンド\]** ウィンドウまたは `/out` スイッチで指定したログ ファイルに表示されます。  
  
## 使用例  
 最初の例では、ソリューション ファイルで指定されている既定の構成を使用して、`MySolution` ソリューションを消去します。  
  
 2 番目の例では、`MySolution` の `Debug` ソリューション構成にある `Debug` プロジェクト ビルド構成を使用して、`CSharpConsoleApp` プロジェクトを消去します。  
  
```  
Devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean  
  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"   
```  
  
## 参照  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)