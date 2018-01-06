---
title: "方法: ワークフロー プロジェクト (レガシ) に新しい項目を追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- sequential workflows, adding to workflow projects
- workflows, adding new items
- state machine workflows, adding to workflow projects
- activities, adding to workflow projects
ms.assetid: 130cd83d-942d-437b-bbb5-8088ec0a6d79
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: add7474c2d38c2cbb06b0d1cc3c92efa0a16c321
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-new-item-to-a-workflow-project-legacy"></a>方法: ワークフロー プロジェクトに新しい項目を追加する (レガシ)
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] が備えている従来の [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]は、[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象としており、これを使用してワークフロー プロジェクトを作成すると、[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 項目や他の一般的な [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 項目をプロジェクトに追加できます。  
  
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
  
## <a name="see-also"></a>参照  
 [従来のワークフロー プロジェクトの作成](../workflow-designer/creating-legacy-workflow-projects.md)