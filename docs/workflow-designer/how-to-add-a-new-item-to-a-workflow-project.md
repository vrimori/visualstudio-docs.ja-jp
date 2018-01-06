---
title: "方法: ワークフロー プロジェクトへ新しい項目の追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: "14"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: e2031f084b11f9879fd94f5d2e454e0966ed3787
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>方法 : ワークフロー プロジェクトへ新しい項目を追加する
ワークフロー プロジェクトを作成した後に、ワークフロー アクティビティ、デザイナーなどの一般的な [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 項目をプロジェクトに追加できます。  
  
 次の表は、ワークフロー プロジェクトに追加できる [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 項目の一覧です。  
  
|名前|説明|  
|----------|-----------------|  
|アクティビティ|他のアクティビティで構成されるアクティビティ。 選択するときに取得されるものとは、同じ XAML ファイルをプロジェクトに追加は、この項目を選択すると、**アクティビティ ライブラリ**新しいプロジェクトのテンプレートです。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]この手順で、次を参照してください。[する方法: アクティビティ ライブラリを作成](../workflow-designer/how-to-create-an-activity-library.md)です。|  
|アクティビティ デザイナー|アクティビティのデザイン時の操作をカスタマイズするデザイナー。 選択するときに取得されるものとは、同じファイルをプロジェクトに追加は、この項目を選択すると、**アクティビティ デザイナー ライブラリ**新しいプロジェクトのテンプレートです。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]この手順で、次を参照してください。[する方法: アクティビティ デザイナー ライブラリを作成](../workflow-designer/how-to-create-an-activity-designer-library.md)です。|  
|Code アクティビティ|コードに記述される実行ロジックを含むアクティビティ。 <xref:System.Activities.CodeActivity.Execute%2A> メソッドのオーバーライドを含むソース コード ファイルは既に自動的に生成されています。|  
|WCF ワークフロー サービス|ワークフロー アクティビティを使用して作成された [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] サービス。 選択するときに取得されるものとは、同じファイルをプロジェクトに追加は、この項目を選択すると、 **WCF ワークフロー サービス アプリケーション**新しいプロジェクトのテンプレートです。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]この手順で、次を参照してください。[する方法: WCF ワークフロー サービス アプリケーションの作成](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md)です。|  
  
### <a name="to-add-a-new-item-to-a-workflow-project"></a>ワークフロー プロジェクトに新しい項目を追加するには  
  
1.  **プロジェクト** メニューのをクリックして**新しい項目の追加.**.  
  
     **新しい項目の追加** ダイアログ ボックスが表示されます。  
  
2.  **インストールされたテンプレート**ペインで、**ワークフロー**グループ。  
  
3.  4 つの項目のいずれかを選択します。 選択可能な項目の一覧が、上記の表に示されています。  
  
4.  内のアイテムの名前を入力、**名前** ダイアログ ボックスの下部にあるボックスです。  
  
5.  をクリックして**追加**現在のワークフロー プロジェクトに、項目を追加します。  
  
## <a name="see-also"></a>参照  
 [ワークフロー プロジェクトの作成](../workflow-designer/creating-a-workflow-project.md)