---
title: カスタム SharePoint プロジェクト項目の種類を定義する |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e4b678d0a4a148bbd8a7414c8a7585b50fbc9c01
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855167"
---
# <a name="define-custom-sharepoint-project-item-types"></a>カスタム SharePoint プロジェクト項目の種類を定義します。
  新しい SharePoint プロジェクト項目の種類を作成する場合は、新しい SharePoint プロジェクト項目の種類を定義します。 たとえば、Visual Studio では、追加のフィールドまたは SharePoint サイトにカスタム アクションの SharePoint プロジェクト アイテムは含まれません。 フィールド、カスタム動作、またはその他の種類の SharePoint コンポーネントを作成するための SharePoint プロジェクト アイテムの独自の型を定義することができます。  
  
## <a name="tasks-for-defining-sharepoint-project-item-types"></a>SharePoint プロジェクト項目の種類を定義するためのタスク
 カスタム プロジェクト項目の種類を定義するアセンブリをビルドする Visual Studio 拡張機能を実装する、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>インターフェイス。 詳細については、「[方法 :SharePoint プロジェクト項目の種類定義](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)します。  
  
 カスタム プロジェクト項目の種類を定義するときに、プロジェクト項目に、次の機能を追加することもできます。  
  
- プロジェクト項目にショートカット メニュー項目を追加します。 プロジェクト項目のショートカット メニューを開くと、メニュー項目が表示される**ソリューション エクスプ ローラー**プロジェクト アイテムを右クリックしてまたは選択するかを選択し、 **Shift** + **F10 キーを押して**キー。 詳細については、「[方法 :ショートカット メニュー項目をカスタム SharePoint プロジェクト項目の種類に追加](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)します。  
  
- プロジェクト項目にカスタム プロパティを追加します。 プロパティを表示する、**プロパティ**ウィンドウで、プロジェクト項目を選択すると**ソリューション エクスプ ローラー**します。 詳細については、「[方法 :カスタム SharePoint プロジェクト項目の種類にプロパティを追加](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)します。  
  
  Visual Studio で、プロジェクト項目を使用するには、他の開発者が有効にする、.spdata ファイルを作成し、プロジェクト項目に関連付けられているプロジェクト テンプレートまたは項目テンプレートを作成します。 詳細については、次を参照してください。[項目テンプレートとの SharePoint プロジェクト アイテムのプロジェクト テンプレートを作成する](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)します。  
  
## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>プロジェクト項目の種類とプロジェクト項目のインスタンス間のリレーションシップを理解します。
 SharePoint プロジェクト項目の種類を定義するときに、Visual Studio は、SharePoint プロジェクトに関連付けられている型のプロジェクト項目が追加されたときに、拡張機能を読み込みます。 例では、新しいを定義する場合の**カスタム アクション**プロジェクト項目の種類、ユーザーを追加するときに、Visual Studio が拡張機能を読み込む、**カスタム アクション**プロジェクトにプロジェクト項目。 Visual Studio では、関連付けられているプロジェクト項目の種類のすべてのインスタンス拡張機能の同じインスタンスを使用します。 ユーザーが 2 つ目を追加する場合、前の例で**カスタム アクション**プロジェクト項目をプロジェクトには、2 つ目のプロジェクト項目をカスタマイズする、拡張機能の同じインスタンスを使用します。  
  
 プロジェクト項目の種類の特定のインスタンスにアクセスするのいずれかの処理、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>のイベント、 *projectItemTypeDefinition*パラメーターの実装で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>メソッド。 たとえば、カスタム型のプロジェクト項目をプロジェクトに追加する場合を判断する処理、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>イベント。 詳細については、「[方法 :SharePoint プロジェクト項目の種類定義](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)します。  
  
## <a name="see-also"></a>関連項目
 [方法: SharePoint プロジェクト項目の種類を定義します。](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [方法: カスタム SharePoint プロジェクト項目の種類にプロパティを追加します。](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [方法: カスタム SharePoint プロジェクト項目の種類のショートカット メニュー項目を追加します。](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [項目テンプレートとの SharePoint プロジェクト アイテムのプロジェクト テンプレートを作成します。](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [チュートリアル: 項目テンプレート、第 1 部でのカスタム動作プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [チュートリアル: プロジェクト テンプレート、第 1 部でサイト列プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [チュートリアル: 項目テンプレート、第 2 部でのカスタム動作プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [チュートリアル: プロジェクト テンプレート、第 2 部でサイト列プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Visual Studio の SharePoint ツールの拡張機能をデプロイします。](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
