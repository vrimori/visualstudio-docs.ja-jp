---
title: "方法 : ワークシート内でデータベースのレコードをスクロールする | Microsoft Docs"
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
  - "データ [Visual Studio での Office 開発], スクロール (データベース レコードを)"
  - "データベース [Visual Studio での Office 開発], スクロール (レコードを)"
  - "レコード [Visual Studio での Office 開発], スクロール"
  - "ワークシート [Visual Studio での Office 開発], スクロール (レコードを)"
ms.assetid: aea4c86c-9d6d-47dd-8977-066e21945dab
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# 方法 : ワークシート内でデータベースのレコードをスクロールする
  次に、デザイナーを使用して Microsoft Office Excel ワークシート内にデータベース テーブルのフィールドを 1 つ表示し、コントロールを使用してエンド ユーザーがすべてのレコードをスクロールできるようにする方法を示します。  
  
 ドキュメント レベルのプロジェクトでは、デザイナーのみを使用できます。  ただし、実行時にプログラムでコントロールを追加し、そのコントロールをデータにバインドすることもできます。  詳細については、「[チュートリアル: VSTO アドイン プロジェクトでの単純データ バインディング](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)」を参照してください。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
### ワークシート内でデータベース レコードをスクロールするには  
  
1.  Visual Studio で Excel アプリケーション プロジェクトを開きます。  
  
2.  **\[データ ソース\]** ウィンドウを開き、データベースからデータ ソースを作成します。  詳細については、「[方法 : データベース内のデータに接続する](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md)」を参照してください。  
  
3.  目的のデータが含まれているテーブルを展開し、特定の列を選択します。  
  
4.  コントロールのリストを開き、**\[NamedRange\]** を選択します。  
  
5.  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを、データを表示するセルにドラッグします。  
  
6.  **ツールボックス**の **\[Windows フォーム\]** タブから <xref:System.Windows.Forms.BindingNavigator> コントロールをワークシートに追加し、使用するコントロールを設定します。  詳細については、「[BindingNavigator コントロールの概要 &#40;Windows フォーム&#41;](../Topic/BindingNavigator%20Control%20Overview%20(Windows%20Forms).md)」を参照してください。  
  
## 参照  
 [Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  