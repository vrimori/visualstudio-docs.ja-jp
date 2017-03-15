---
title: "ワークフロー デザイナーでワークフローにコメントを追加する方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Presentation.Annotations.Annotation.UI"
  - "Annotation"
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
caps.latest.revision: 7
caps.handback.revision: 5
ms.author: "sdanie"
manager: "erikre"
---
# ワークフロー デザイナーでワークフローにコメントを追加する方法
より大きく複雑なワーク フローを作成を容易にするために、[!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] では開発者が次の種類のデザイナーの項目に注釈を追加できます。  
  
-   <xref:System.Activities.Activity>  
  
-   <xref:System.Activities.Statements.State>  
  
-   <xref:System.Activities.Statements.Transition>  
  
-   <xref:System.Activities.Statements.FlowNode> の派生クラス  
  
-   <xref:System.Activities.Variable>  
  
-   <xref:System.Activities.Argument>  
  
> [!IMPORTANT]
>  注釈の内容はワーク フローに関連付けられた XAML ファイルにテキスト形式で保存され、他のユーザーが読み取る可能性があります。注釈に機密情報を入力する場合は注意してください。  
  
### デザイナーのアクティビティへの注釈の追加  
  
1.  ワークフロー デザイナーで、ワークフロー デザイナーの項目を右クリックし、**\[注釈\]**、**\[注釈の追加\]** をクリックします。  
  
2.  注釈のテキストを提供された領域に追加します。  
  
3.  項目に注釈アイコンが表示されます。注釈アイコン上にカーソルを置くと、注釈のテキストが表示されます。  
  
     ![Sequence アクティビティで注釈を表示している](../debugger/debug-interface-access/annotation.md "Annotation")  
  
### アクティビティのデザイナーへの注釈の表示  
  
1.  アクティビティの外部に注釈を表示するアクティビティ デザイナーで、注釈の装飾の**ピン** アイコンをクリックします。  
  
2.  注釈がアクティビティ デザイナーに表示されます。次スクリーンショットでは、「ワーク フローのアクティビティを開始する」という注釈がアクティビティ デザイナーに表示されています。  
  
     ![注釈がアクティビティ デザイナーに表示されている](../workflow-designer/media/annotationindesigner.png "AnnotationInDesigner")  
  
3.  アクティビティ デザイナーの外部に注釈を表示するには、アクティビティのデザイナーの注釈の領域にカーソルを置き、**ピン解除**アイコンをクリックします。  
  
     ![注釈がアクティビティ デザイナーの外部に表示されている](../workflow-designer/media/annotationoutsidedesigner.png "AnnotationOutsideDesigner")  
  
### すべての注釈の表示または非表示  
  
1.  注釈を持つアクティビティを右クリックします。**\[注釈\]**、**\[すべての注釈を表示\]** をクリックします。  
  
2.  すべての注釈がアクティビティのデザイナーに表示されます。  
  
3.  アクティビティのデザイナーの外部のすべての注釈を表示するには、アクティビティを右クリックし、**\[注釈\]**、**\[すべての注釈を非表示\]** をクリックします。  
  
### アクティビティの注釈の編集または削除  
  
1.  注釈を持つアクティビティを右クリックします。  
  
2.  **\[注釈\]**、**\[注釈の編集\]** または **\[注釈の削除\]** をクリックします。  
  
3.  編集または削除用に注釈が開きます。  
  
4.  すべての注釈を一度に削除するには、ワークフロー デザイナーを右クリックし、**\[注釈\]**、**\[すべての注釈を削除\]** をクリックします。  
  
### 変数または引数の注釈の追加、編集、削除  
  
1.  変数または引数を右クリックし、\[注釈の追加\] をクリックします。  
  
2.  注釈のテキストを入力します。変数または引数に注釈アイコンが表示されます。  
  
3.  注釈を持つ変数または引数を右クリックします。\[注釈の編集\] をクリックします。  
  
4.  編集用に注釈が開きます。  
  
5.  注釈を持つ変数または引数を右クリックします。\[注釈の削除\] をクリックします。  
  
6.  注釈が削除されます。