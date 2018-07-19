---
title: ワークフロー内でのサポートをフォーム |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9b3a07f56819818e55548292f3dbcdc1095d9f00
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326081"
---
# <a name="form-support-in-workflows"></a>ワークフロー内でのフォームのサポート
  次の 4 つの種類のフォームをワークフローで使用できます: アソシエーション、開始、タスク、および変更します。 これらのフォーム型は、ASPX フォームまたは InfoPath フォームのいずれかに基づいて作成できます。 レベルをサポートする[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]は特定のフォームは、次の表で説明されているいくつかの要因によって異なります。 ワークフローの形式の種類の詳細については、次を参照してください。[ワークフロー フォームの概要](http://go.microsoft.com/fwlink/?LinkId=185228)MSDN Web サイト。  
  
## <a name="xml-refactoring"></a>XML のリファクタリング
 ASPX アソシエーションまたは開始フォームを追加すると、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ワークフロー プロジェクト項目、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]でワークフローの XML を自動的にリファクタリング*Elements.xml*アソシエーションに参照する属性を保持するファイルまたは、同期フォームの名前または配置パスが更新されるたびに開始フォームまたはフォームを削除します。 ただし、タスクまたは変更フォームなど、ワークフロー内の他のフォームの種類を使用すると、 *Elements.xml*ファイルをリファクタリングできません。  
  
## <a name="form-support-in-new-visual-studio-workflows"></a>新しい Visual Studio ワークフローでのフォームのサポート
 次の表[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]内に作成されるワークフロー内の ASPX または InfoPath のフォーム上のさまざまなフォーム型のサポート[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。  
  
|フォームの種類|ASPX フォームを使用して Visual Studio で作成したワークフロー|InfoPath フォームを使用して Visual Studio で作成したワークフロー|  
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|  
|関連付け|ASPX の関連付けフォームを使用して、ワークフローに追加できる、**ワークフロー関連付けフォーム**項目テンプレート。<br />- *Elements.xml*フォームの追加、名前の変更、または削除すると、ときに、またはその配置パスが変更されたときに、ワークフローのファイルをリファクタリングします。<br />詳細については、次を参照してください。[チュートリアル: 関連付けと開始フォームを持つワークフローを作成する](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)します。|InfoPath フォーム テンプレートをアソシエーションではありません-しない[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。<br />間の統合は-ありません[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]および InfoPath デザイナー。<br />- *Elements.xml*ワークフローのファイルをリファクタリングできません。|  
|開始|-ASPX 開始フォームを使用して、ワークフローに追加できる、**ワークフロー開始フォーム**項目テンプレート。<br />- *Elements.xml*フォームの追加、名前の変更、または削除すると、ときに、またはその配置パスが変更されたときに、ワークフローのファイルをリファクタリングします。<br />詳細については、次を参照してください。[チュートリアル: 関連付けと開始フォームを持つワークフローを作成する](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)します。|InfoPath フォーム テンプレートをアソシエーションではありません-しない[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。<br />間の統合は-ありません[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]および InfoPath デザイナー。<br />- *Elements.xml*ワークフローのファイルをリファクタリングできません。|  
|タスク|ASPX タスク フォームのテンプレートが表示されます-[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。 アプリケーション ページを作成し、コードを追加する必要があります。<br />- *Elements.xml*ワークフローのファイルをリファクタリングできません。<br />詳細については、次を参照してください[ワークフロー タスク フォーム (SharePoint foundation 2010)。](http://go.microsoft.com/fwlink/?LinkId=187674)|InfoPath フォーム テンプレートをタスクではありません-しない[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。<br />間の統合は-ありません[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]および InfoPath デザイナー。<br />- *Elements.xml*ワークフローのファイルをリファクタリングできません。|  
|変更|ASPX の変更フォーム テンプレートが表示されます-[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。 修正フォームを追加するには、アプリケーション ページを作成し、コードを追加する必要があります。<br />- *Elements.xml*ワークフローのファイルをリファクタリングできません。 必要に応じて手動で編集する必要があります。<br />詳細については、次を参照してください[ワークフロー変更フォーム (SharePoint foundation 2010)。](http://go.microsoft.com/fwlink/?LinkId=187675)|InfoPath フォーム テンプレートを変更ではありません-しない[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。<br />間の統合は-ありません[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]および InfoPath デザイナー。<br />- *Elements.xml*ワークフローのファイルをリファクタリングできません。|  
  
## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>インポートされた SharePoint の再利用可能なワークフローでのフォームのサポート
 次の表[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]にインポートされる SharePoint の再利用可能なワークフローで ASPX または InfoPath のフォーム上のさまざまなフォーム型のサポート[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。  
  
|フォームの種類|SharePoint Designer からインポートされた ASPX フォームを含む再利用可能なワークフロー|SharePoint Designer からインポートされた InfoPath フォームを含む再利用可能なワークフロー|  
|---------------|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|関連付け|フォームが参照されている、 *Elements.xml*ワークフローのファイル。<br />- *Elements.xml*形式の名前を変更または削除すると、ときに、またはその配置パスが変更されたときに、ワークフローのファイルをリファクタリングします。|-フォームは、インポートしますが、で参照されていない、 *Elements.xml*のワークフロー。<br />- *Elements.xml*ワークフローのファイルをリファクタリングできません。|  
|開始|-フォームが、ワークフローによって参照されている、 *Elements.xml*ワークフローのファイル。<br />- *Elements.xml*形式の名前を変更または削除すると、ときに、またはその配置パスが変更されたときに、ワークフローのファイルをリファクタリングします。|-フォームは、インポートしますが、で参照されていない、 *Elements.xml*のワークフロー。<br />- *Elements.xml*ワークフローのファイルをリファクタリングできません。 **注:** 規則およびプロパティを追加およびこのシナリオを実現するための変更する必要があります。|  
|タスク|フォームが参照されている、 *Elements.xml*ワークフローのファイル。<br />- *Elements.xml*ワークフローのファイルをリファクタリングできません。|-フォームは、インポートしますが、で参照されていない、 *Elements.xml*のワークフロー。<br />- *Elements.xml*ワークフローのファイルをリファクタリングできません。 **注:** 規則およびプロパティを追加およびこのシナリオを実現するための変更する必要があります。|  
|変更|該当なし。 SharePoint Designer では、ASPX 修正フォームを作成できません。|該当なし。 除く組み込みの SharePoint サーバーのワークフローは、ワークフローをエクスポートするとき、.wsp ファイルには含まれません SharePoint designer、InfoPath 修正フォームを作成できません。|  
  
## <a name="see-also"></a>関連項目
 [チュートリアル: 関連付けフォームと開始フォームとワークフローを作成します。](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [SharePoint ワークフロー ソリューションを作成します。](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [既存の SharePoint サイトからアイテムをインポートします。](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  
