---
title: "方法: ワークフロー プロジェクトに新しい項目を追加する (レガシ) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "アクティビティ, ワークフロー プロジェクトへの追加"
  - "シーケンシャル ワークフロー, ワークフロー プロジェクトへの追加"
  - "ステート マシン ワークフロー, ワークフロー プロジェクトへの追加"
  - "ワークフロー, 新しい項目の追加"
ms.assetid: 130cd83d-942d-437b-bbb5-8088ec0a6d79
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 方法: ワークフロー プロジェクトに新しい項目を追加する (レガシ)
[!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] が備えている従来の [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]は、[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象としており、これを使用してワークフロー プロジェクトを作成すると、[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 項目や他の一般的な [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 項目をプロジェクトに追加できます。  
  
 次の表は、ワークフロー プロジェクトに追加できる [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] 項目の一覧です。  
  
|項目|説明|  
|--------|--------|  
|アクティビティ|デザイナー コード ファイル内にアクティビティ定義が含まれ、別のコード ファイル内にユーザー コードが含まれるアクティビティ。|  
|アクティビティ \(コード分離付き\)|ワークフロー マークアップとして表記されたアクティビティ定義と、別のコード ファイル内のユーザー コード。|  
|シーケンシャル ワークフロー \(コード\)|デザイナー コード ファイル内にワークフロー定義が含まれ、別のコード ファイル内にユーザー コードが含まれるシーケンシャル ワークフロー。|  
|シーケンシャル ワークフロー \(コード分離付き\)|ワークフロー定義がワークフロー マークアップとして表記され、別のコード ファイル内にユーザー コードが含まれるシーケンシャル ワークフロー。|  
|ステート マシンのワークフロー \(コード\)|デザイナー コード ファイル内にワークフロー定義が含まれ、別のコード ファイル内にユーザー コードが含まれるステート マシン ワークフロー。|  
|ステート マシンのワークフロー \(コード分離付き\)|ワークフロー定義がワークフロー マークアップとして表記され、別のコード ファイル内にユーザー コードが含まれるステート マシン ワークフロー。|  
  
### ワークフロー プロジェクトに新しい項目を追加するには  
  
1.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
     **\[新しい項目の追加\]** ダイアログ ボックスが表示されます。  
  
2.  項目を選択します。  
  
     選択可能な Windows Workflow Foundation 項目の一覧が、上記の表に示されています。  
  
3.  **\[追加\]** をクリックして、ワークフロー プロジェクトに項目を追加します。  
  
## 参照  
 [従来のワークフロー プロジェクトの作成](../workflow-designer/creating-legacy-workflow-projects.md)