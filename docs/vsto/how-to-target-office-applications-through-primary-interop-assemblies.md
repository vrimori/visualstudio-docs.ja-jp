---
title: "方法 : プライマリ相互運用機能アセンブリを利用して Office アプリケーションを使用する | Microsoft Docs"
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
  - "アプリケーション開発 [Visual Studio での Office 開発], 自動化"
  - "アセンブリ [Visual Studio での Office 開発], PIA 参照"
  - "Office アプリケーション [Visual Studio での Office 開発], 自動化"
  - "Visual Studio の Office プライマリ相互運用アセンブリ, 追加 (参照を)"
  - "プライマリ相互運用機能アセンブリ [Visual Studio での Office 開発], 追加 (参照を)"
ms.assetid: 9bedae85-32b6-4df6-82b2-9d124fb49636
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# 方法 : プライマリ相互運用機能アセンブリを利用して Office アプリケーションを使用する
  新しい Office プロジェクトを作成すると、Visual Studio により、そのプロジェクトのビルドに必要な Microsoft Office プライマリ相互運用機能アセンブリ \(PIA: Primary Interop Assembly\) への参照が自動的に追加されます。  次の場合は、他の PIA への参照を追加する必要があります。  
  
-   プロジェクトで他の Microsoft Office アプリケーションの機能を使用する。  たとえば、Microsoft Office Word プロジェクトで Microsoft Office Excel の機能を使用することが必要になる場合があります。  
  
-   Microsoft Office Access など、Visual Studio に専用のプロジェクトがない Microsoft Office アプリケーションを自動化する。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### プライマリ相互運用機能アセンブリに参照を追加するには  
  
1.  Office プロジェクトを開き、**ソリューション エクスプローラー**でプロジェクト名を選択します。  
  
2.  **\[プロジェクト\]** メニューの **\[参照の追加\]** をクリックします。  
  
3.  **\[Framework\]** タブの **\[コンポーネント名\]** ボックスの一覧で、使用する PIA を選択します。  用意されている Microsoft Office プライマリ相互運用機能アセンブリの詳細については、「[Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)」を参照してください。  
  
     プロジェクトが [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象としている場合は、アセンブリ参照の **\[相互運用型の埋め込み\]** プロパティが既定で **\[True\]** に設定されます。  この設定を使用すると、ソリューションはエンド ユーザーのコンピューターに PIA を必要としません。  詳細については、「[Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)」を参照してください。  
  
    > [!NOTE]  
    >  Office プロジェクトで、**\[参照の追加\]** ダイアログ ボックスの **\[COM\]** タブではなく **\[.NET\]** タブを使用して、必ず Office PIA への参照を追加します。  詳細については、「[Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)」を参照してください。  
  
4.  **\[OK\]** をクリックします。  
  
     アセンブリ名が**ソリューション エクスプローラー**の **\[参照設定\]** フォルダーに表示されます。  
  
## 参照  
 [Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)   
 [Office ソリューションのコードの記述](../vsto/writing-code-in-office-solutions.md)   
 [Office ソリューションの開発](../vsto/developing-office-solutions.md)   
 [方法 : Office のプライマリ相互運用機能アセンブリをインストールする](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  