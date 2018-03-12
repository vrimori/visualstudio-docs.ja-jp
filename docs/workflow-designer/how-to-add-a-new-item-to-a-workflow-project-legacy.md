---
title: "方法: ワークフロー プロジェクト (レガシ) に新しい項目を追加 |Microsoft ドキュメント"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- sequential workflows, adding to workflow projects
- workflows, adding new items
- state machine workflows, adding to workflow projects
- activities, adding to workflow projects
ms.assetid: 130cd83d-942d-437b-bbb5-8088ec0a6d79
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d2b0c644854f8f08ff7aeeb05f92fe3fd359f45e
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-a-new-item-to-a-workflow-project-legacy"></a>方法: ワークフロー プロジェクトに新しい項目を追加する (レガシ)
によって提供される従来の Windows ワークフロー デザイナーを使用して、ワークフロー プロジェクトを作成した後[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]をターゲットとするか、[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)]または[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]、追加することができます[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]項目やその他の一般的な[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]アイテムをプロジェクトです。

 次の表は、ワークフロー プロジェクトに追加できる [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] 項目の一覧です。

|アイテム|説明|
|----------|-----------------|
|アクティビティ|デザイナー コード ファイル内にアクティビティ定義が含まれ、別のコード ファイル内にユーザー コードが含まれるアクティビティ。|
|アクティビティ (コード分離付き)|ワークフロー マークアップとして表記されたアクティビティ定義と、別のコード ファイル内のユーザー コード。|
|シーケンシャル ワークフロー (コード)|デザイナー コード ファイル内にワークフロー定義が含まれ、別のコード ファイル内にユーザー コードが含まれるシーケンシャル ワークフロー。|
|シーケンシャル ワークフロー (コード分離付き)|ワークフロー定義がワークフロー マークアップとして表記され、別のコード ファイル内にユーザー コードが含まれるシーケンシャル ワークフロー。|
|ステート マシンのワークフロー (コード)|デザイナー コード ファイル内にワークフロー定義が含まれ、別のコード ファイル内にユーザー コードが含まれるステート マシン ワークフロー。|
|ステート マシンのワークフロー (コード分離付き)|ワークフロー定義がワークフロー マークアップとして表記され、別のコード ファイル内にユーザー コードが含まれるステート マシン ワークフロー。|

### <a name="to-add-a-new-item-to-a-workflow-project"></a>ワークフロー プロジェクトに新しい項目を追加するには

1.  **プロジェクト** メニューのをクリックして**新しい項目の追加**です。

     **新しい項目の追加** ダイアログ ボックスが表示されます。

2.  項目を選択します。

     選択可能な Windows Workflow Foundation 項目の一覧が、上記の表に示されています。

3.  をクリックして**追加**ワークフロー プロジェクトに、項目を追加します。

## <a name="see-also"></a>関連項目

- [従来のワークフロー プロジェクトの作成](../workflow-designer/creating-legacy-workflow-projects.md)