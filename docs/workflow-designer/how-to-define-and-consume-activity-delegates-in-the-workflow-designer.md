---
title: "ワークフロー デザイナーでアクティビティ デリゲートを定義および使用する方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
ms.author: "sdanie"
manager: "erikre"
caps.handback.revision: 3
---
# ワークフロー デザイナーでアクティビティ デリゲートを定義および使用する方法
[!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] には、すぐに使用できる <xref:System.Activities.Statements.InvokeDelegate> アクティビティの新しいデザイナーが含まれています。このデザイナーは、<xref:System.Activities.ActivityAction> や <xref:System.Activities.ActivityFunc%601> など、<xref:System.Activities.ActivityDelegate> から派生するアクティビティにデリゲートを割り当てるために使用できます。  
  
### アクティビティ デリゲートを定義する  
  
1.  [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] で、**\[ファイル\]**、**\[新規作成\]**、**\[プロジェクト\]** の順にクリックします。左の **\[ワークフロー\]** ノードと右の **\[ワークフロー コンソール アプリケーション\]** テンプレートをクリックします。プロジェクトに名前を付け \(必要な場合\)、**\[OK\]** をクリックします。  
  
2.  **ソリューション エクスプローラー**でプロジェクトを右クリックし、**\[追加\]**、**\[新しい項目\]** をクリックします。左の **\[ワークフロー\]** ノードと右の **\[アクティビティ\]** テンプレートをクリックします。新しいアクティビティに「**MyForEach.xaml**」という名前を付け、**\[OK\]** をクリックします。アクティビティによってワークフロー デザイナーが開きます。  
  
3.  ワークフロー デザイナーで **\[引数\]** タブをクリックします。  
  
4.  **\[引数の作成\]** をクリックします。新しい引数に「**Items**」という名前を付けます。  
  
5.  **\[引数の型\]** 列で **\[配列: \[T\]\]** をクリックします。  
  
6.  型ブラウザーで **\[オブジェクト\]** をクリックします。**\[OK\]** をクリックします。  
  
7.  **\[引数の作成\]** を再度クリックします。新しい引数に「**Body**」という名前を付けます。新しい引数の **\[方向\]** 列で **\[プロパティ\]** をクリックします。  
  
8.  \[引数の型\] 列で **\[型の参照\]** をクリックします。  
  
9. 型ブラウザーで**型名**フィールドに「**ActivityAction**」と入力します。ツリー ビューで **\[ActivityAction\<T\>\]** をクリックします。表示されるドロップダウンで **\[オブジェクト\]** をクリックし、**ActivityAction\<Object\>** 型を引数に割り当てます。  
  
10. <xref:System.Activities.Statements.While> アクティビティを、ツールボックスの **\[制御フロー\]** セクションからデザイナー画面にドラッグします。  
  
11. <xref:System.Activities.Statements.While> アクティビティを選択し、**\[変数\]** タブをクリックします。  
  
12. **\[変数の作成\]** をクリックします。新しい変数に「**Index**」という名前を付けます。  
  
13. **\[変数の型\]** 列で **\[Int32\]** をクリックします。**\[スコープ\]** を **\[While\]**、**\[既定\]** 列を空欄のままにします。  
  
14. <xref:System.Activities.Statements.While> アクティビティの**条件**プロパティの値を **index \< Items.Length;** に設定します。  
  
15. <xref:System.Activities.Statements.InvokeDelegate> アクティビティを、ツールボックスの **\[プリミティブ\]** セクションから <xref:System.Activities.Statements.While> アクティビティの **\[本文\]** にドラッグします。  
  
16. デリゲート ドロップダウン リストで **\[本文\]** をクリックします。  
  
17. <xref:System.Activities.Statements.InvokeDelegate> アクティビティの **\[プロパティ\]** グリッドで、**デリゲートの引数**プロパティの **\[...\]** をクリックします。  
  
18. 「**Argument**」という引数の **\[値\]** 列に「**Items\[Index\]**」と入力します。**\[OK\]** をクリックして **\[デリゲートの引数\]** ダイアログ ボックスを閉じます。  
  
19. <xref:System.Activities.Statements.Assign> アクティビティを <xref:System.Activities.Statements.InvokeDelegate> アクティビティの下の水平線にドラッグします。<xref:System.Activities.Statements.Assign> アクティビティが作成されます。**MyForEach** アクティビティの **\[本文\]** セクションの 2 つのアクティビティを含むように、<xref:System.Activities.Statements.Sequence> アクティビティが自動的に作成されます。**\[本文\]** セクションは 1 つのアクティビティだけを含めることができるため、シーケンスが必要になります。自動的に新しい <xref:System.Activities.Statements.Sequence> アクティビティを作成することは [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] の新機能です。  
  
20. <xref:System.Activities.Statements.Assign> アクティビティの**追加先**プロパティを **index** に設定します。**Assign** アクティビティの**値**プロパティを **index\+1** に設定します。  
  
 カスタムの **MyForEach** アクティビティは、**Items** コレクションを通じて渡された値ごとに任意のアクティビティを 1 回呼び出し、コレクションの値をアクティビティの入力として使用します。  
  
### ワーク フローにカスタム アクティビティを使用する  
  
1.  **Ctrl** キーと **Shift** キーを押しながら **B** キーを押して、プロジェクトをビルドします。  
  
2.  **ソリューション エクスプローラー**で、デザイナーの **Workflow1.xaml** を開きます。  
  
3.  **MyForEach** アクティビティをツールボックスからデザイナー画面にドラッグします。アクティビティは、プロジェクトと同じ名前のツールボックスのセクションにあります。  
  
4.  **MyForEach** アクティビティの**項目**プロパティを **new Object\[\] {1, "abc"}** に設定します。  
  
5.  <xref:System.Activities.Statements.WriteLine> アクティビティを、ツールボックスの **\[プリミティブ\]** セクションから **MyForEach** アクティビティの **\[デリゲート:本文\]** セクションにドラッグします。  
  
6.  <xref:System.Activities.Statements.WriteLine> アクティビティの**テキスト** プロパティを **Argument.ToString\(\)** に設定します。  
  
 ワーク フローの実行時に、コンソールには次のように表示されます。  
  
 **1**   
**abc**