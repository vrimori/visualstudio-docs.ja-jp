---
title: "方法: Office ソリューションを開発できるようにコンピューターを構成する | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio での Office 開発, インストール (ツールの)"
  - "必要条件 [Visual Studio での Office 開発]"
ms.assetid: 76b463dc-43f0-47a1-845b-fe0a5e14bd80
caps.latest.revision: 130
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 129
---
# 方法: Office ソリューションを開発できるようにコンピューターを構成する
  Visual Studio の Microsoft Office Developer Tools を使用できるように開発コンピューターを構成するには、次のトピックの手順を実行します。  これらの手順を実行するには、開発コンピューターの管理特権を保持している必要があります。  
  
### 開発コンピューターを構成するには  
  
1.  Office Developer Tools が含まれているバージョンの Visual Studio をインストールします。  Office 開発者ツールは既定でインストールされます。  インストールする機能を選択して Visual Studio のインストールをカスタマイズする場合は、セットアップ時に **\[Microsoft Office Developer Tools\]** を選択していることを確認してください。 Office Developer Tools が含まれているバージョンの Visual Studio の詳細については、「[Office ソリューションを開発できるようにコンピューターを構成する](../vsto/configuring-a-computer-to-develop-office-solutions.md)」を参照してください。  
  
2.  Visual Studio の Office Developer Tools によってサポートされているバージョンの Office をインストールします。  詳細については、「[Office ソリューションを開発できるようにコンピューターを構成する](../vsto/configuring-a-computer-to-develop-office-solutions.md)」を参照してください。  
  
     インストールするバージョンの Office の PIA もインストールされることを確認してください。  PIA は、既定では Office と共にインストールされます。  Office セットアップを変更する場合は、対象とするアプリケーションに対して **.NET プログラミング サポート**機能が選択されていることを確認します。  
  
3.  Windows の言語を英語以外に設定している状態で英語版の Visual Studio を使用する場合は、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] の Language Pack をインストールすることにより、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] のメッセージを Windows と同じ言語で表示できます。  英語版以外の Visual Studio では、この言語パックが自動的にインストールされます。  言語パックは、「[Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkId=140386)」から入手できます。  
  
## 参照  
 [Office 開発の新機能](http://msdn.microsoft.com/ja-jp/bf054af2-c896-4723-aa15-6381145b14bb)   
 [はじめに &#40;Visual Studio での Office 開発&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [方法: Visual Studio Tools for Office の再頒布可能なランタイムをインストールする](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)   
 [方法 : Office のプライマリ相互運用機能アセンブリをインストールする](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  