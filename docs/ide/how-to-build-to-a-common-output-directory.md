---
title: "方法 : 共通出力ディレクトリへのビルド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ビルド [Visual Studio], 共通のディレクトリ"
  - "共通のディレクトリ"
  - "出力ディレクトリ"
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# 方法 : 共通出力ディレクトリへのビルド
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

既定では、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は、ソリューション内の各プロジェクト用のフォルダーの中にプロジェクトをビルドします。  プロジェクトのビルド出力パスを変更して、すべてのビルドを同じフォルダーに出力できます。  
  
### すべてのソリューション出力を共通ディレクトリに配置するには  
  
1.  ソリューションのプロジェクトをクリックします。  
  
2.  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
3.  プロジェクトの種類に応じて、**\[コンパイル\]** タブ、または **\[ビルド\]** タブのどちらかをクリックし、**\[出力パス\]** をそのソリューションのすべてのプロジェクトが使用するフォルダーに設定します。  
  
4.  ソリューションのすべてのプロジェクトに対して、手順 1 ～ 3 を繰り返します。  
  
## 参照  
 [Visual Studio でのアプリケーションのビルド](../ide/compiling-and-building-in-visual-studio.md)   
 [方法 : ビルド出力ディレクトリを変更する](../ide/how-to-change-the-build-output-directory.md)