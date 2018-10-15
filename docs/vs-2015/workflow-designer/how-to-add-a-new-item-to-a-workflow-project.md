---
title: '方法: ワークフロー プロジェクトへ新しい項目の追加 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f9dd186c4f9b319b5c4c60fa48d3a32e16c673f3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210941"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>方法 : ワークフロー プロジェクトへ新しい項目を追加する
ワークフロー プロジェクトを作成した後に、ワークフロー アクティビティ、デザイナーなどの一般的な [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 項目をプロジェクトに追加できます。  
  
 次の表は、ワークフロー プロジェクトに追加できる [!INCLUDE[wf](../includes/wf-md.md)] 項目の一覧です。  
  
|名前|説明|  
|----------|-----------------|  
|アクティビティ|他のアクティビティで構成されるアクティビティ。 この項目を選択を選択するときに取得される、プロジェクトに同じ XAML ファイルを追加、**アクティビティ ライブラリ**新しいプロジェクトのテンプレート。 [!INCLUDE[crabout](../includes/crabout-md.md)] この手順では、次を参照してください。[方法: アクティビティ ライブラリを作成](../workflow-designer/how-to-create-an-activity-library.md)です。|  
|アクティビティ デザイナー|アクティビティのデザイン時の操作をカスタマイズするデザイナー。 この項目を選択を選択するときに取得される、プロジェクトに同じファイルを追加、**アクティビティ デザイナー ライブラリ**新しいプロジェクトのテンプレート。 [!INCLUDE[crabout](../includes/crabout-md.md)] この手順では、次を参照してください。[方法: アクティビティ デザイナー ライブラリを作成](../workflow-designer/how-to-create-an-activity-designer-library.md)です。|  
|Code アクティビティ|コードに記述される実行ロジックを含むアクティビティ。 <xref:System.Activities.CodeActivity.Execute%2A> メソッドのオーバーライドを含むソース コード ファイルは既に自動的に生成されています。|  
|WCF ワークフロー サービス|ワークフロー アクティビティを使用して作成された [!INCLUDE[indigo2](../includes/indigo2-md.md)] サービス。 この項目を選択を選択するときに取得される、プロジェクトに同じファイルを追加、 **WCF ワークフロー サービス アプリケーション**新しいプロジェクトのテンプレート。 [!INCLUDE[crabout](../includes/crabout-md.md)] この手順では、次を参照してください。[方法: WCF ワークフロー サービス アプリケーションの作成](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md)です。|  
  
### <a name="to-add-a-new-item-to-a-workflow-project"></a>ワークフロー プロジェクトに新しい項目を追加するには  
  
1.  **プロジェクト** メニューのをクリックして**新しい項目の追加.**.  
  
     **新しい項目の追加** ダイアログ ボックスが表示されます。  
  
2.  **インストールされたテンプレート**ペインで、**ワークフロー**グループ。  
  
3.  4 つの項目のいずれかを選択します。 選択可能な項目の一覧が、上記の表に示されています。  
  
4.  内の項目の名前を入力、**名前** ダイアログ ボックスの下部にあるボックス。  
  
5.  クリックして**追加**現在ワークフロー プロジェクトに項目を追加します。  
  
## <a name="see-also"></a>関連項目  
 [ワークフロー プロジェクトの作成](../workflow-designer/creating-a-workflow-project.md)