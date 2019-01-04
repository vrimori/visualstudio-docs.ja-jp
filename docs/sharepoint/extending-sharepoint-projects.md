---
title: SharePoint プロジェクトの拡張 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2cc42ed418de78ee5f75ab51b63c7e1ccdf29911
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53863983"
---
# <a name="extend-sharepoint-projects"></a>SharePoint プロジェクトを拡張します。
  SharePoint プロジェクトのプロジェクト レベルの機能をカスタマイズする場合は、プロジェクトの拡張機能を作成します。 たとえば、カスタム プロジェクトのプロパティ を追加したり、ユーザーは、Visual Studio で SharePoint ソリューションを開発するときに発生するプロジェクト レベルのイベントに応答することができます。  
  
## <a name="create-project-extensions"></a>プロジェクトの拡張機能を作成します。
 プロジェクト項目を拡張するアセンブリをビルドする Visual Studio 拡張機能を実装する、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>インターフェイス。 詳細については、「[方法 :SharePoint プロジェクト拡張機能作成](../sharepoint/how-to-create-a-sharepoint-project-extension.md)です。  
  
 プロジェクトの拡張機能を作成するときに、SharePoint プロジェクトに、次の機能を追加することもできます。  
  
- ショートカット メニュー項目を追加します。 SharePoint プロジェクト ノードのショートカット メニューを開くと、メニュー項目が表示される**ソリューション エクスプ ローラー**ノードを右クリックし、選択または選択、 **Shift** + **F10 キーを押して**キー。 詳細については、「[方法 :ショートカット メニュー項目を SharePoint プロジェクトに追加](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)します。  
  
- カスタム プロパティを追加します。 プロパティを表示する、**プロパティ**ウィンドウで、SharePoint プロジェクトを選択すると**ソリューション エクスプ ローラー**します。 詳細については、「[方法 :SharePoint プロジェクトにプロパティを追加](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)します。  
  
  作成、展開、およびプロジェクトの拡張機能をテストする方法について説明するチュートリアルでは、次を参照してください。[チュートリアル。SharePoint プロジェクト拡張機能作成](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)です。  
  
## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>プロジェクトの拡張機能とプロジェクトのインスタンス間のリレーションシップを理解します。
 任意の種類の SharePoint プロジェクトを開いたときに、拡張機能を読み込むプロジェクトの拡張機能を作成するときに[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] リスト定義、コンテンツの種類、イベント レシーバーなどのいくつかの SharePoint プロジェクト テンプレートが含まれています。 ただし、これには 1 つだけの SharePoint プロジェクトの種類があります。 表示されるプロジェクトの種類、**新しいプロジェクト** ダイアログ ボックスは、1 つまたは複数の SharePoint プロジェクト項目を一緒にバンドルするテンプレートのみです。 SharePoint プロジェクトの種類を 1 つだけなので、1 つのプロジェクトを作成した拡張機能は、すべての SharePoint プロジェクトに適用されます。 たとえば、のみに適用される拡張機能を作成することはできません、**コンテンツの種類**プロジェクト。  
  
 特定のプロジェクト インスタンスにアクセスするのいずれかの処理、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents>のイベント、 *projectService*パラメーターの実装で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>メソッド。 たとえば、SharePoint プロジェクトがソリューションに追加されたときを特定する処理、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded>イベント。 詳細については、「[方法 :SharePoint プロジェクト拡張機能作成](../sharepoint/how-to-create-a-sharepoint-project-extension.md)です。  
  
## <a name="see-also"></a>関連項目
 [方法: SharePoint プロジェクト拡張機能を作成します。](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [方法: SharePoint プロジェクトのショートカット メニュー項目を追加します。](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [方法: SharePoint プロジェクトにプロパティを追加します。](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [チュートリアル: SharePoint プロジェクト拡張機能を作成します。](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [カスタム SharePoint プロジェクト項目の種類を定義します。](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [SharePoint プロジェクト項目を拡張します。](../sharepoint/extending-sharepoint-project-items.md)   
 [SharePoint のパッケージ化と配置を拡張します。](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [SharePoint プロジェクト システムを拡張します。](../sharepoint/extending-the-sharepoint-project-system.md)  
