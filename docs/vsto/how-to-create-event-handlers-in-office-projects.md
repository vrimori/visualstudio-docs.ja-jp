---
title: "方法: Office プロジェクトでイベント ハンドラーを作成する"
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
  - "イベント ハンドラー [Visual Studio での Office 開発]"
  - "イベント [Visual Studio での Office 開発]"
  - "Visual Basic [Visual Studio での Office 開発], イベント ハンドラー"
  - "Visual C# [Visual Studio での Office 開発], イベント ハンドラー"
ms.assetid: 2cfd6a45-4c25-4431-b4fc-e0f2c0a72e54
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# 方法: Office プロジェクトでイベント ハンドラーを作成する
  Visual Basic および C\# でイベント ハンドラーを作成するには、いくつかの方法があります。  デザイン ビューでは、コントロールをダブルクリックしてコントロールの既定のイベント ハンドラーを作成でき、**\[プロパティ\]** ウィンドウのイベント ペインを使用してコントロール上のイベントを処理するハンドラーを作成することもできます。  ただし、コード ビューでは、イベント ハンドラーを作成するためにデザイン ビューに切り替えることはありません。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### Visual Basic でイベント ハンドラーを作成するには  
  
1.  コード エディターの上部にある **\[クラス名\]** のドロップダウン リストで、イベント ハンドラーを作成するオブジェクトを選択します。  
  
    > [!NOTE]  
    >  `ThisDocument` または `ThisWorkbook` のイベント ハンドラーを作成する場合は、**\[クラス名\]** のドロップダウン リストで、**\[\(ThisDocument イベント\)\]** または **\[\(ThisWorkbook イベント\)\]** を選択する必要があります。  
  
2.  コード エディターの上部にある **\[メソッド名\]** のドロップダウン リストで、イベントを選択します。  
  
     イベント ハンドラーが作成され、新規作成されたイベント ハンドラーにカーソルが移動します。  イベント ハンドラーが既に存在する場合は、既存のイベント ハンドラーにカーソルが移動します。  
  
### C\# でイベント ハンドラーを作成するには  
  
1.  修飾されたイベント名に続けて空白を入力し、次に空白を含まずに「\+\=」を入力することによって、クラスの **Startup** イベントにイベント デリゲートを作成します。  次に例を示します。  
  
     `this.<object name>.<event name> +=`  
  
2.  コード行の末尾で、Tab キーを 2 回押します。  
  
     コード行が自動的に完了し、新規作成されたイベント ハンドラーにカーソルが移動します。  
  
## 参照  
 [Office ソリューションのコードの記述](../vsto/writing-code-in-office-solutions.md)   
 [チュートリアル : NamedRange コントロールのイベントのプログラミング  
](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Office ソリューションのビルド](../vsto/building-office-solutions.md)  
  
  