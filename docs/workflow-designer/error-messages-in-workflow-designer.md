---
title: "ワークフロー デザイナーでのエラー メッセージ |Microsoft ドキュメント"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 748893d7e08ca72140fad31c4546f4166636b8de
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="error-messages-in-workflow-designer"></a>ワークフロー デザイナーでのエラー メッセージ
このトピックでは、Windows ワークフロー デザイナーを使用する場合に発生する可能性のあるエラー メッセージの種類について説明します。

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>ワークフロー デザイナーでエラーが発生する状況
 以下の場合に、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]のエラーが発生します。

1.  式でエラーが発生している。

2.  アクティビティの検証制約が満たされていない。

3.  アクティビティによる読み込み失敗を引き起こすエラーが XAML ファイルで発生している。

4.  ワークフローによる読み込み失敗を引き起こすエラーが XAML ファイルで発生している。

 無効な式や検証制約違反によって、ワークフローの構築が失敗することはありません。 ワークフローは正常に構築されますが、実行時に <xref:System.Activities.InvalidWorkflowException> がスローされます。 XAML ファイルにエラーがある場合は、構築が失敗します。

 内部[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ワークフローが読み込まれるときに、そのエラーに表示されます、**エラー一覧**です。 エラーの原因となったアクティビティに移動するでエラーをダブルクリックして、**エラー一覧**です。

### <a name="expression-errors"></a>式のエラー
 無効な式が赤い円で示され、その式の横に白い感嘆符が付いています。 このアイコンの上にカーソルを置くと、エラーの原因を表すツールヒントが表示されます。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内では、式をクリックすると、エラーの発生元に下線が引かれた行が表示されます。 下線が引かれたテキストの上にカーソルを置くと、エラーの発生元を示すツールヒントが表示されます。

### <a name="activity-validation-errors"></a>アクティビティ検証エラー
 アクティビティの検証制約に違反する場合は、赤い円と白い感嘆符がアクティビティの右上角に表示されます。 このアイコンの上にカーソルを置くと、エラーの原因を表すツールヒントが表示されます。

### <a name="xaml-load-errors"></a>XAML 読み込みエラー
 アクティビティは、読み込みに失敗した場合、テキストを「アクティビティ読み込めませんでした、XAML でエラーがあるため」赤いボックスが表示されます。 これは通常、アクティビティの型を解決できない場合に発生します。 デザイナーで赤いボックスを選択して、それを削除すると、無効なアクティビティを削除できます。

### <a name="workflow-load-errors"></a>ワークフロー読み込みエラー
 ワークフローは、読み込みに失敗すると、ワークフローの読み込み失敗の原因となった例外情報と共に、デザイナー サーフェイス「ドキュメントで問題をワークフロー デザイナーが発生しました」というテキストが表示されます。 通常、これは、XAML ファイルを解析できない場合に発生します。