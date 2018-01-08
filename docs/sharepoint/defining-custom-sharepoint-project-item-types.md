---
title: "カスタム SharePoint プロジェクト項目の種類の定義 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
ms.assetid: be300c24-fd1b-4fc7-a4e9-a5df1d81d3fc
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: e627d78e5c040614c29e7503cd7efab728b02bfa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="defining-custom-sharepoint-project-item-types"></a>SharePoint プロジェクト項目の種類の定義
  新しい SharePoint プロジェクト項目の種類を作成するときに、新しい SharePoint プロジェクト項目の種類を定義します。 たとえば、Visual Studio では、フィールドの追加または SharePoint サイトにカスタム アクションの SharePoint プロジェクト項目は含まれません。 SharePoint プロジェクト項目のフィールド、カスタム アクション、またはその他の種類の SharePoint コンポーネントを作成するための独自の型を定義することができます。  
  
## <a name="tasks-for-defining-sharepoint-project-item-types"></a>SharePoint プロジェクト項目の種類を定義するためのタスク  
 カスタム プロジェクト項目の種類を定義するアセンブリをビルドする Visual Studio 拡張機能を実装する、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>インターフェイスです。 詳細については、次を参照してください。[する方法: SharePoint プロジェクト項目の種類を定義する](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)です。  
  
 カスタム プロジェクト項目の種類を定義するときは、プロジェクト項目に、次の機能を追加することもできます。  
  
-   プロジェクト項目にショートカット メニュー項目を追加します。 プロジェクト項目のショートカット メニューを開くと、メニュー項目が表示される**ソリューション エクスプ ローラー**キーをプロジェクト項目を右クリックするか選択し、shift キーを押しながら F10 を選択します。 詳細については、次を参照してください。[する方法: カスタム SharePoint プロジェクト項目の種類へのショートカット メニュー項目の追加](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)です。  
  
-   プロジェクト項目にカスタム プロパティを追加します。 このプロパティを表示、**プロパティ**でプロジェクト項目を選択するときにウィンドウ**ソリューション エクスプ ローラー**です。 詳細については、次を参照してください。[する方法: カスタム SharePoint プロジェクト項目の種類にプロパティを追加](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)です。  
  
 その他の開発者が Visual Studio でプロジェクト項目を使用するには、.spdata ファイルを作成し、項目テンプレートまたはプロジェクト項目に関連付けられているプロジェクト テンプレートを作成します。 詳細については、次を参照してください。[項目テンプレートを作成し、SharePoint プロジェクト項目用のプロジェクト テンプレート](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)です。  
  
## <a name="understanding-the-relationship-between-project-item-types-and-project-item-instances"></a>プロジェクト項目の種類とプロジェクト項目のインスタンス間の関係を理解します。  
 SharePoint プロジェクト項目の種類を定義するときに、Visual Studio は、関連付けられている型のプロジェクト アイテムが SharePoint プロジェクトに追加されたときに、拡張機能を読み込みます。 新しいを定義する場合など、**カスタム アクション**プロジェクト項目の種類、ユーザーを追加すると、Visual Studio は拡張機能を読み込む、**カスタム アクション**プロジェクトにプロジェクト項目です。 Visual Studio では、関連付けられているプロジェクト項目の種類のすべてのインスタンスの拡張機能の同じインスタンスを使用します。 ユーザーが、2 番目を追加する場合、前の例で**カスタム アクション**プロジェクト項目をプロジェクトには、2 つ目のプロジェクト アイテムをカスタマイズする、拡張機能の同じインスタンスを使用します。  
  
 プロジェクト項目の種類の特定のインスタンスにアクセスするのいずれかの処理、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>のイベント、 *projectItemTypeDefinition*の実装でのパラメーター、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>メソッドです。 たとえば、調べるには、カスタム型のプロジェクト アイテムをプロジェクトに追加するときに、処理、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>イベント。 詳細については、次を参照してください。[する方法: SharePoint プロジェクト項目の種類を定義する](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)です。  
  
## <a name="see-also"></a>参照  
 [方法: SharePoint プロジェクト項目の種類の定義](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [方法: カスタム SharePoint プロジェクト項目の種類にプロパティを追加](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [方法: カスタム SharePoint プロジェクト項目の種類へのショートカット メニュー項目の追加](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [SharePoint プロジェクト項目の項目テンプレートとプロジェクト テンプレートを作成します。](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [チュートリアル: 項目テンプレート、第 1 部にカスタム動作プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [チュートリアル: プロジェクト テンプレート、第 1 部に基づくサイト列プロジェクト項目の作成](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [チュートリアル: 項目テンプレート、第 2 部にカスタム動作プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [チュートリアル: プロジェクト テンプレート、第 2 部に基づくサイト列プロジェクト項目の作成](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Visual Studio での SharePoint ツールの拡張機能の配置](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  