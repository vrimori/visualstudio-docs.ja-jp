---
title: "ワークフロー デザイナーでのエラー メッセージ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "WFDErrorMessages.UI"
  - "System.Activities.Presentation.ErrorActivity.UI"
  - "System.Activities.Presentation.View.ErrorView.UI"
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# ワークフロー デザイナーでのエラー メッセージ
ここでは、[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]で作業しているときに生成される可能性のあるエラー メッセージの種類について説明します。  
  
## ワークフロー デザイナーでエラーが発生する状況  
 以下の場合に、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]のエラーが発生します。  
  
1.  式でエラーが発生している。  
  
2.  アクティビティの検証制約が満たされていない。  
  
3.  アクティビティによる読み込み失敗を引き起こすエラーが XAML ファイルで発生している。  
  
4.  ワークフローによる読み込み失敗を引き起こすエラーが XAML ファイルで発生している。  
  
 無効な式や検証制約違反によって、ワークフローの構築が失敗することはありません。ワークフローは正常に構築されますが、実行時に <xref:System.Activities.InvalidWorkflowException> がスローされます。XAML ファイルにエラーがある場合は、構築が失敗します。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内では、ワークフローが読み込まれたときに、そのエラーが **\[エラー一覧\]** に表示されます。エラーの発生元であるアクティビティに移動するには、**\[エラー一覧\]** でエラーをダブルクリックします。  
  
### 式のエラー  
 無効な式が赤い円で示され、その式の横に白い感嘆符が付いています。このアイコンの上にカーソルを置くと、エラーの発生元を示すツールヒントが表示されます。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内では、式をクリックすると、エラーの発生元に下線が引かれた行が表示されます。下線が引かれたテキストの上にカーソルを置くと、エラーの発生元を示すツールヒントが表示されます。  
  
### アクティビティ検証エラー  
 アクティビティの検証制約に違反する場合は、赤い円と白い感嘆符がアクティビティの右上角に表示されます。このアイコンの上にカーソルを置くと、エラーの原因を表すツールヒントが表示されます。  
  
### XAML 読み込みエラー  
 アクティビティで読み込みが失敗すると、"XAML 内のエラーのため、アクティビティを読み込むことができませんでした" というテキストが表示された赤いボックスが開きます。通常、これは、アクティビティの型が解決できない場合に発生します。デザイナーで赤いボックスを選択して、それを削除すると、無効なアクティビティを削除できます。  
  
### ワークフロー読み込みエラー  
 ワークフローで読み込みに失敗した場合は、"ワークフロー デザイナーはドキュメントで問題を検出しました" というテキストと、ワークフロー読み込みの障害の原因となった例外の情報がデザイナー画面に表示されます。通常、これは、XAML ファイルを解析できない場合に発生します。