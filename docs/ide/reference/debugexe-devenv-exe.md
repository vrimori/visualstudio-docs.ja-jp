---
title: "/DebugExe (devenv.exe) | Microsoft Docs"
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
  - "/DebugExe [devenv.exe]"
  - "DebugExe スイッチ"
  - "Devenv, /DebugExe スイッチ"
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定した実行可能ファイルをデバッグするために開きます。  
  
## 構文  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## 引数  
 `ExecutableFile`  
 必ず指定します。  .exe ファイルのパスとファイル名。  
  
 .exe ファイルが見つからない場合、または存在しない場合は、警告やエラーは表示されず、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] は通常どおり起動します。  
  
## 解説  
 `ExecutableFile` パラメーターに続くどの文字列もそのファイルに引数として受け取られます。  
  
## 使用例  
 デバックするために `MyApplication.exe` ファイルを開く例を次に示します。  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## 参照  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)