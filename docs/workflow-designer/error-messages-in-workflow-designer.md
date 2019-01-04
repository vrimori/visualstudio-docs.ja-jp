---
title: ワークフロー デザイナーでのエラー メッセージ
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 393157c11029a36038b3fea0fa78af413d650ef3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53871396"
---
# <a name="error-messages-in-workflow-designer"></a>ワークフロー デザイナーでのエラー メッセージ

このトピックでは、ワークフロー デザイナーを使用する場合に発生する可能性のあるエラー メッセージの種類について説明します。

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>ワークフロー デザイナーでエラーが発生する状況

ワークフロー デザイナーでのエラーは、次の状況で発生します。

1.  式でエラーが発生している。

2.  アクティビティの検証制約が満たされていない。

3.  アクティビティによる読み込み失敗を引き起こすエラーが XAML ファイルで発生している。

4.  ワークフローによる読み込み失敗を引き起こすエラーが XAML ファイルで発生している。

無効な式や検証制約違反によって、ワークフローの構築が失敗することはありません。 ワークフローは正常に構築されますが、実行時に <xref:System.Activities.InvalidWorkflowException> がスローされます。 XAML ファイルにエラーがある場合は、構築が失敗します。

Visual Studio 内でワークフローが読み込まれるときにそのエラーに表示されます、**エラー一覧**します。 エラーの原因であるアクティビティに移動するでエラーをダブルクリックして、**エラー一覧**します。

### <a name="expression-errors"></a>式のエラー
 無効な式が赤い円で示され、その式の横に白い感嘆符が付いています。 このアイコンの上にカーソルを置くと、エラーの原因を表すツールヒントが表示されます。 Visual Studio 内には、エラーの原因で下線を表示する行を表示する式をクリックします。 下線が引かれたテキストの上にカーソルを置くと、エラーの発生元を示すツールヒントが表示されます。

### <a name="activity-validation-errors"></a>アクティビティ検証エラー
 アクティビティの検証制約に違反する場合は、赤い円と白い感嘆符がアクティビティの右上角に表示されます。 このアイコンの上にカーソルを置くと、エラーの原因を表すツールヒントが表示されます。

### <a name="xaml-load-errors"></a>XAML 読み込みエラー
 アクティビティは、読み込みに失敗した場合、テキスト「アクティビティ読み込めませんでした、XAML のエラーにより」赤いボックスが表示されます。 これは通常、アクティビティの型を解決できない場合に発生します。 デザイナーで赤いボックスを選択して、それを削除すると、無効なアクティビティを削除できます。

### <a name="workflow-load-errors"></a>ワークフロー読み込みエラー
 ワークフローの読み込みに失敗、ワークフローの読み込み失敗の原因となった例外情報と共に、デザイナー画面に「ドキュメントで問題をワークフロー デザイナーが発生しました」というテキストが表示されます。 通常、これは、XAML ファイルを解析できない場合に発生します。