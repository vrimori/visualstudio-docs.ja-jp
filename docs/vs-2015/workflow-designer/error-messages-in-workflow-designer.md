---
title: ワークフロー デザイナーでのエラー メッセージ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: efd6bc680be42f1074da8d2313b1a4b8e9307580
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894847"
---
# <a name="error-messages-in-workflow-designer"></a>ワークフロー デザイナーでのエラー メッセージ
ここでは、[!INCLUDE[wfd1](../includes/wfd1-md.md)]で作業しているときに生成される可能性のあるエラー メッセージの種類について説明します。  
  
## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>ワークフロー デザイナーでエラーが発生する状況  
 以下の場合に、[!INCLUDE[wfd2](../includes/wfd2-md.md)]のエラーが発生します。  
  
1. 式でエラーが発生している。  
  
2. アクティビティの検証制約が満たされていない。  
  
3. アクティビティによる読み込み失敗を引き起こすエラーが XAML ファイルで発生している。  
  
4. ワークフローによる読み込み失敗を引き起こすエラーが XAML ファイルで発生している。  
  
   無効な式や検証制約違反によって、ワークフローの構築が失敗することはありません。 ワークフローは正常に構築されますが、実行時に <xref:System.Activities.InvalidWorkflowException> がスローされます。 XAML ファイルにエラーがある場合は、構築が失敗します。  
  
   内部[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ワークフローが読み込まれるときに、そのエラーに表示されます、**エラー一覧**します。 エラーの原因であるアクティビティに移動するでエラーをダブルクリックして、**エラー一覧**します。  
  
### <a name="expression-errors"></a>式のエラー  
 無効な式が赤い円で示され、その式の横に白い感嘆符が付いています。 このアイコンの上にカーソルを置くと、エラーの原因を表すツールヒントが表示されます。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 内では、式をクリックすると、エラーの発生元に下線が引かれた行が表示されます。 下線が引かれたテキストの上にカーソルを置くと、エラーの発生元を示すツールヒントが表示されます。  
  
### <a name="activity-validation-errors"></a>アクティビティ検証エラー  
 アクティビティの検証制約に違反する場合は、赤い円と白い感嘆符がアクティビティの右上角に表示されます。 このアイコンの上にカーソルを置くと、エラーの原因を表すツールヒントが表示されます。  
  
### <a name="xaml-load-errors"></a>XAML 読み込みエラー  
 アクティビティで読み込みが失敗すると、"XAML 内のエラーのため、アクティビティを読み込むことができませんでした" というテキストが表示された赤いボックスが開きます。 通常、これは、アクティビティの型が解決できない場合に発生します。 デザイナーで赤いボックスを選択して、それを削除すると、無効なアクティビティを削除できます。  
  
### <a name="workflow-load-errors"></a>ワークフロー読み込みエラー  
 ワークフローで読み込みに失敗した場合は、"ワークフロー デザイナーはドキュメントで問題を検出しました" というテキストと、ワークフロー読み込みの障害の原因となった例外の情報がデザイナー画面に表示されます。 通常、これは、XAML ファイルを解析できない場合に発生します。