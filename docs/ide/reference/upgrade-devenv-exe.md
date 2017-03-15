---
title: "/Upgrade (devenv.exe) | Microsoft Docs"
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
  - "/upgrade DEVENV スイッチ"
  - "Devenv, /upgrade スイッチ"
  - "upgrade DEVENV スイッチ"
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ソリューション ファイルおよびそのすべてのプロジェクト ファイル、または指定されたプロジェクト ファイルを、そのファイルに対応する現在の [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の形式に更新します。  
  
## 構文  
  
```  
devenv SolutionFile | ProjectFile /upgrade  
```  
  
## 引数  
 `SolutionFile`  
 ソリューションおよびそのプロジェクト全体をアップグレードする場合は必須です。  ソリューション ファイルのパスと名前です。  ソリューション ファイルの名前のみを入力するか、完全パスと名前を入力できます。  存在しないフォルダー名やファイル名を入力した場合は、フォルダーやファイルが作成されます。  
  
 `ProjectFile`  
 単一のプロジェクトをアップグレードする場合、必須です。  ソリューション内のプロジェクト ファイルのパスと名前です。  プロジェクト ファイルの名前のみを入力するか、完全パスと名前を入力できます。  存在しないフォルダー名やファイル名を入力した場合は、フォルダーやファイルが作成されます。  
  
## 解説  
 バックアップは自動的に作成され、現在のディレクトリに作成される Backup という名前のディレクトリにコピーされます。  
  
 ソース管理されたソリューションまたはプロジェクトは、アップグレードする前にチェックアウトする必要があります。  
  
 `/upgrade` スイッチを使用した場合、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] は起動されません。  アップグレードの結果は、ソリューションまたはプロジェクトの開発言語のアップグレード レポートで参照できます。  エラーや使用方法は返されません。  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] でプロジェクトをアップグレードする方法の詳細については、「[方法: Visual Studio プロジェクトのアップグレードが成功しなかった場合のトラブルシューティング](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)」を参照してください。  
  
## 使用例  
 この例では、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ソリューションの既定フォルダーにある "MyProject.sln" という名前のソリューション ファイルをアップグレードします。  
  
```  
devenv "MyProject.sln" /upgrade  
```  
  
## 参照  
 [方法: Visual Studio プロジェクトのアップグレードが成功しなかった場合のトラブルシューティング](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)   
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)