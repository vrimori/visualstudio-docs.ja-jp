---
title: "方法 : Office のプライマリ相互運用機能アセンブリをインストールする"
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
  - "Office プライマリ相互運用機能アセンブリ, インストール"
  - "プライマリ相互運用機能アセンブリ [Visual Studio での Office 開発], インストール"
ms.assetid: 92948fcc-76c6-4b08-ba63-cab59dd60eb1
caps.latest.revision: 61
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 60
---
# 方法 : Office のプライマリ相互運用機能アセンブリをインストールする
  Microsoft Office のインストール時に、Office のプライマリ相互運用機能アセンブリ \(PIA\) をインストールします。  
  
### Office のインストール時に PIA をインストールするには  
  
1.  .NET Framework のバージョンが 2.0 以降であることを確認します。  
  
2.  Microsoft Office をインストールします。このとき、拡張するアプリケーションの **.NET プログラミング サポート**機能が選択されていることを確認します \(この機能は既定のインストールに含まれています\)。  
  
    > [!WARNING]  
    >  既定では、ソリューションのビルド時に、PIA がそのソリューションに埋め込まれるため、VSTO アドインまたはカスタマイズを使用するための前提条件として、PIA をユーザーに配布する必要はありません。  
  
## 参照  
 [Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)   
 [方法 : プライマリ相互運用機能アセンブリを利用して Office アプリケーションを使用する](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [方法: Office ソリューションを開発できるようにコンピューターを構成する](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [方法: Visual Studio Tools for Office の再頒布可能なランタイムをインストールする](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)   
 [Office ソリューションの開発の概要 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [はじめに &#40;Visual Studio での Office 開発&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
  
  