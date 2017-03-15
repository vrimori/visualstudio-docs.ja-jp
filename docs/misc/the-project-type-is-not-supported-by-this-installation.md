---
title: "このプロジェクトの種類は、このインストールではサポートされていません。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.projectflavornotavailable"
ms.assetid: 50e92aff-3ce9-4600-94af-4a16e9dffc90
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# このプロジェクトの種類は、このインストールではサポートされていません。
このエラーは、Visual Studio と共にインストールされないソフトウェア開発キット \(SDK\) を必要とする種類のプロジェクトを開こうとすると発生します。  たとえば、Visual Studio SDK がインストールされていないコンピューターで Visual Studio を開き、VSIX プロジェクトなど、その SDK のプロジェクト ファイルを開こうとすると、このエラーが発生します \(Visual Studio SDK の詳細については、「[Visual Studio を機能拡張する](http://go.microsoft.com/fwlink/?LinkID=64968)」を参照してください\)。  
  
## 回避策  
 開こうとしているプロジェクトの種類に合った正しい SDK がインストールされていることを確認する必要があります。  
  
#### 既に SDK がインストールされているかどうかを確認するには  
  
1.  メニュー バーで **\[ファイル\]**、**\[新規\]**、**\[プロジェクト\]** の順にクリックします。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスで、**\[インストール済み\]** ノード、**\[テンプレート\]** ノードの順に展開し、**\[その他のプロジェクトの種類\]** ノードをクリックします。  
  
3.  開こうとしているプロジェクトが使用できるかどうかを判断するために、使用できるプロジェクトの種類を確認します。  
  
 開こうとしているプロジェクトの種類が見つからない場合、関連付けられた SDK がインストールされていません。  そのプロジェクトの種類を開くには、関連付けられた SDK を見つけてインストールする必要があります。  
  
## 参照  
 [Visual Studio 2015 の新機能](../ide/what-s-new-in-visual-studio-2015.md)   
 [Visual Studio プロジェクトの移植、移行、およびアップグレード](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)