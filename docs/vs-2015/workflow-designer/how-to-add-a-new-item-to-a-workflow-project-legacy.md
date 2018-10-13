---
title: '方法: ワークフロー プロジェクト (レガシ) に新しい項目の追加 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sequential workflows, adding to workflow projects
- workflows, adding new items
- state machine workflows, adding to workflow projects
- activities, adding to workflow projects
ms.assetid: 130cd83d-942d-437b-bbb5-8088ec0a6d79
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 26be9519a4f9ee496ea36a61debffec7f96ffbe5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49301159"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project-legacy"></a>方法: ワークフロー プロジェクトに新しい項目を追加する (レガシ)
[!INCLUDE[wfd1](../includes/wfd1-md.md)] が備えている従来の [!INCLUDE[vs2010](../includes/vs2010-md.md)]は、[!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] または [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] を対象としており、これを使用してワークフロー プロジェクトを作成すると、[!INCLUDE[wf](../includes/wf-md.md)] 項目や他の一般的な [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 項目をプロジェクトに追加できます。  
  
 次の表は、ワークフロー プロジェクトに追加できる [!INCLUDE[wf2](../includes/wf2-md.md)] 項目の一覧です。  
  
|アイテム|説明|  
|----------|-----------------|  
|アクティビティ|デザイナー コード ファイル内にアクティビティ定義が含まれ、別のコード ファイル内にユーザー コードが含まれるアクティビティ。|  
|アクティビティ (コード分離付き)|ワークフロー マークアップとして表記されたアクティビティ定義と、別のコード ファイル内のユーザー コード。|  
|シーケンシャル ワークフロー (コード)|デザイナー コード ファイル内にワークフロー定義が含まれ、別のコード ファイル内にユーザー コードが含まれるシーケンシャル ワークフロー。|  
|シーケンシャル ワークフロー (コード分離付き)|ワークフロー定義がワークフロー マークアップとして表記され、別のコード ファイル内にユーザー コードが含まれるシーケンシャル ワークフロー。|  
|ステート マシンのワークフロー (コード)|デザイナー コード ファイル内にワークフロー定義が含まれ、別のコード ファイル内にユーザー コードが含まれるステート マシン ワークフロー。|  
|ステート マシンのワークフロー (コード分離付き)|ワークフロー定義がワークフロー マークアップとして表記され、別のコード ファイル内にユーザー コードが含まれるステート マシン ワークフロー。|  
  
### <a name="to-add-a-new-item-to-a-workflow-project"></a>ワークフロー プロジェクトに新しい項目を追加するには  
  
1.  **プロジェクト** メニューのをクリックして**新しい項目の追加**します。  
  
     **新しい項目の追加** ダイアログ ボックスが表示されます。  
  
2.  項目を選択します。  
  
     選択可能な Windows Workflow Foundation 項目の一覧が、上記の表に示されています。  
  
3.  クリックして**追加**ワークフロー プロジェクトに項目を追加します。  
  
## <a name="see-also"></a>関連項目  
 [従来のワークフロー プロジェクトの作成](../workflow-designer/creating-legacy-workflow-projects.md)