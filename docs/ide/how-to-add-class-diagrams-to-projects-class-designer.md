---
title: "How to: Add Class Diagrams to Projects (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "class diagrams, creating"
  - "Class Designer [Visual Studio], opening"
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# How to: Add Class Diagrams to Projects (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

クラスおよび他の型の設計、編集およびリファクタリングを行うには、クラス ダイアグラムを Visual C\# .NET、Visual Basic .NET、または C\+\+ プロジェクトに追加します。  プロジェクト内のコードの異なる部分を視覚化するには、複数のクラス ダイアグラムをプロジェクトに追加します。  
  
 複数のアプリでコードを共有しているプロジェクトからは、クラス ダイアグラムを作成できません。  UML クラス ダイアグラムを作成するには、「[UML モデリング プロジェクトおよびダイアグラムを作成する](../modeling/create-uml-modeling-projects-and-diagrams.md)」を参照してください。  
  
### プロジェクトに空のクラス ダイアグラムを追加するには  
  
1.  ソリューション エクスプローラーで、プロジェクト名を右クリックします。  次に、**\[新しい項目の追加\]** または **\[追加\]**、**\[新しい項目\]** をクリックします。  
  
2.  テンプレートの一覧から、**\[クラス ダイアグラム\]** を選択します。  Visual C\+\+ のプロジェクトの場合、このテンプレートを見つけるには、**\[テンプレート\]** の下にある **\[ユーティリティ\]** を探します。  
  
     クラス デザイナーでクラス ダイアグラムが開き、ソリューション エクスプローラーのプロジェクト階層に .cd 拡張子付きのファイルとして表示されます。  図形や線をダイアグラムにドラッグするには、クラス デザイナーのツールボックスを使用します。  
  
3.  複数のクラス ダイアグラムを追加するには、この手順を繰り返します。  
  
### 既存の型に基づいてクラス ダイアグラムを追加するには  
  
1.  ソリューション エクスプローラーで、クラス ファイル コンテキスト メニューを開き、**\[クラス ダイアグラムの表示\]** をクリックします。  
  
     または  
  
     **\[クラス ビュー\]** で、名前空間または型のコンテキスト メニューを開き、**\[クラス ダイアグラムで表示\]** を選択します。  
  
### クラス ダイアグラムに完全なプロジェクトの内容を表示するには  
  
1.  ソリューション エクスプローラーまたは \[クラス ビュー\] で、プロジェクトを右クリックし、**\[表示\]**、**\[クラス ダイアグラムで表示\]** の順に選択します。  
  
     自動設定されたクラス ダイアグラムが作成されます。  
  
## 参照  
 [How to: Create Types by using Class Designer](../ide/how-to-create-types-by-using-class-designer.md)   
 [How to: View Existing Types \(Class Designer\)](../Topic/How%20to:%20View%20Existing%20Types%20\(Class%20Designer\).md)   
 [Designing Classes and Types \(Class Designer\)](../ide/designing-classes-and-types-class-designer.md)   
 [Viewing Types and Relationships \(Class Designer\)](../ide/viewing-types-and-relationships-class-designer.md)   
 [Working with Class Diagrams \(Class Designer\)](../ide/working-with-class-diagrams-class-designer.md)