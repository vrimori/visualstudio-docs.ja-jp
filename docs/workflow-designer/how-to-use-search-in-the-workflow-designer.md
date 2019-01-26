---
title: '方法: ワークフロー デザイナーで検索を使用する'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: b8a7a58e51706b5bd4d353595487984dd137c361
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55043389"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>方法: ワークフロー デザイナーで検索を使用する

大規模でより複雑なワークフローを作成するためには、キーワードで項目を検索するワークフロー デザイナー内で検索できます。 デザイナーでは、置換はサポートされないことに注意してください。

## <a name="quick-find"></a>クイック検索

クイック検索では、デザイナーで、次を検索します。

-   <xref:System.Activities.Activity> オブジェクト、<xref:System.Activities.Statements.FlowNode> オブジェクト、<xref:System.Activities.Statements.State> オブジェクト、遷移、およびその他のカスタム フロー制御項目のプロパティ。

-   変数

-   引数

-   式

### <a name="use-quick-find"></a>クイック検索を使用します。

1. ワークフロー デザイナーを開いた状態で、キーを押します**Ctrl + F**、または選択**編集** > **検索し、置換** > **クイック検索**.

2. 検索用語を入力してください、**検索**テキスト ボックス をクリック**次を検索**します。

3. 検索用語は、現在のワークフローにあります。 次の図は、デザイナー内に配置されているアクティビティの表示名を示しています。

   ![ワークフロー デザイナーでの検索結果](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>フォルダーを指定して検索する

ファイルには、検索は、XAML ファイルを含むワークフロー ファイル内の文字列を検索します。

### <a name="use-find-in-files"></a>ファイルの検索を使用してください。

1.  Visual Studio で、キーを押します**Ctrl**+**Shift**+**F**、または選択**編集** >  。**検索し、置換** > **ファイル内の検索**します。

2.  検索項目を入力してください、**検索**テキスト ボックス をクリック**すべて検索**します。

3.  検索結果に示されます、**の検索結果**ビュー。 結果の項目をダブルクリックするとは、ワークフロー デザイナーで一致を含むアクティビティに移動します。