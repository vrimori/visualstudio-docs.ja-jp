---
title: "方法 : Office ソリューションの構成情報を設定する"
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
  - "構成ファイル [Visual Studio での Office 開発]"
  - "ソリューション [Visual Studio での Office 開発], 構成ファイル"
ms.assetid: f123838f-957a-4cf5-acc0-0cc0f4c2aea2
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# 方法 : Office ソリューションの構成情報を設定する
  構成ファイルを使用して、各 Office ソリューションに固有の設定を構成できます。  アセンブリ バインディング ポリシー、オブジェクトのリモート処理、デバッグ、トレースの設定などを指定できます。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### Office プロジェクトに構成ファイルを追加するには  
  
1.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
2.  **カテゴリ** ペインで、**\[全般\]** をクリックします。  
  
3.  **\[テンプレート\]** ペインの **\[アプリケーション構成ファイル\]** をクリックします。  
  
4.  **\[ファイル名\]** ボックスで、アセンブリと同じ名前を入力し、拡張子 .config を付けます。  たとえば、ExcelWorkbook1.dll という Excel プロジェクト アセンブリの構成ファイルの場合は、ExcelWorkbook1.dll.config という名前になります。  
  
5.  **\[追加\]** をクリックします。  
  
6.  アプリケーション構成ファイル スキーマに従って構成ファイルを作成します。  詳細については、「[.NET Framework の構成ファイル スキーマ](../Topic/Configuration%20File%20Schema%20for%20the%20.NET%20Framework.md)」を参照してください。  
  
 Office プロジェクトでの構成ファイルの使用に関して特に注意する点はありません。  
  
## 参照  
 [.NET Framework の構成ファイル スキーマ](../Topic/Configuration%20File%20Schema%20for%20the%20.NET%20Framework.md)   
 [Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)  
  
  