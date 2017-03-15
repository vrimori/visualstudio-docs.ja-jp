---
title: "/Log (devenv.exe) | Microsoft Docs"
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
  - "/Log Devenv スイッチ"
  - "Devenv, /Log スイッチ"
  - "Log スイッチ [devenv.exe]"
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Log (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

すべてのアクティビティをトラブルシューティング用のログ ファイルに記録します。  このファイルは、`devenv /log` を少なくとも 1 回呼び出した後に表示されます。  ログ ファイルは既定で次のものになります。  
  
 *%APPDATA%*\\Microsoft\\VisualStudio\\*Version*\\ActivityLog.xml  
  
 ここで、*Version* は Visual Studio のバージョンです。  ただし、別のパスとファイル名を指定することもできます。  
  
## 構文  
  
```  
Devenv /log Path\NameOfLogFile  
```  
  
## 解説  
 このスイッチは、その他すべてのスイッチの後、コマンド ラインの末尾に指定する必要があります。  
  
 ログは、\/log スイッチで呼び出した Visual Studio のすべてのインスタンスを対象として記録されます。  スイッチなしで呼び出した Visual Studio のインスタンスについてはログ記録の対象外です。  
  
## 参照  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)