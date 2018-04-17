---
title: ワークフローでのサポートを形成 |Microsoft ドキュメント
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
ms.openlocfilehash: b06f956cec9f26aff59089be4e29affcd6d73ad8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="form-support-in-workflows"></a>ワークフローでのフォームのサポート
  次の 4 つの種類のフォームをワークフローで使用できます: アソシエーション、開始に使用する、タスク、および変更します。 これらのフォーム型は、ASPX フォームまたはフォームのいずれかに基づいて作成できます。 レベルをサポートする[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]特定のフォームは、次の表で説明されるいくつかの要因によって異なります。 を提供します。 フォームの種類のワークフローの詳細については、次を参照してください。[ワークフロー フォームの概要](http://go.microsoft.com/fwlink/?LinkId=185228)MSDN Web サイトです。  
  
## <a name="xml-refactoring"></a>XML のリファクタリング  
 ASPX アソシエーションまたは開始フォームを追加すると、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ワークフロー プロジェクト項目、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]の同期の関連付けまたは開始フォームを参照する属性を保持するワークフローの Elements.xml ファイル内の XML が自動的にリファクタリングしました。フォームの名前または配置パスを更新するたびにまたはフォームを削除します。 ただし、タスクまたは更新フォームなどのワークフローで他のフォームの種類を使用すると、Elements.xml ファイルいないリファクターされています。  
  
## <a name="form-support-in-new-visual-studio-workflows"></a>Visual Studio の新しいワークフローでのフォームのサポート  
 次の表にリスト[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]で作成したワークフローの ASPX または InfoPath のフォーム上のさまざまなフォーム型のサポート[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。  
  
|フォームの種類|ASPX フォームでの Visual Studio で作成したワークフロー|InfoPath フォームを使用して Visual Studio で作成されたワークフロー|  
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|  
|関連付け|ASPX の関連付けフォームを使用して、ワークフローに追加できる、**ワークフロー関連付けフォーム**項目テンプレート。<br />-ワークフローの Elements.xml ファイルは、フォームの追加、名前変更、または削除すると、ときに、またはその配置パスが変更されたときにリファクターされています。<br />詳細については、次を参照してください。[チュートリアル: アソシエーションと開始フォームを使用するワークフローを作成する](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)です。|テンプレートはありません。 InfoPath の関連付けフォームで[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。<br />-がない間の統合[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]および InfoPath デザイナー。<br />-ワークフローの Elements.xml ファイルをリファクタリングできません。|  
|開始に使用します。|-使用して、ワークフローに ASPX 開始フォームを追加することができます、**ワークフロー開始フォーム**項目テンプレート。<br />-ワークフローの Elements.xml ファイルは、フォームの追加、名前変更、または削除すると、ときに、またはその配置パスが変更されたときにリファクターされています。<br />詳細については、次を参照してください。[チュートリアル: アソシエーションと開始フォームを使用するワークフローを作成する](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)です。|テンプレートはありません。 InfoPath の関連付けフォームで[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。<br />-がない間の統合[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]および InfoPath デザイナー。<br />-ワークフローの Elements.xml ファイルをリファクタリングできません。|  
|タスク|ASPX タスク フォームのテンプレートで使用できる[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。 アプリケーション ページを作成し、コードを追加する必要があります。<br />-ワークフローの Elements.xml ファイルをリファクタリングできません。<br />詳細については、次を参照してください[ワークフロー タスク フォーム (SharePoint Foundation)。](http://go.microsoft.com/fwlink/?LinkId=187674)|テンプレートはありません。 InfoPath タスク フォームで[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。<br />-がない間の統合[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]および InfoPath デザイナー。<br />-ワークフローの Elements.xml ファイルをリファクタリングできません。|  
|変更|ASPX の変更のフォーム テンプレートがある-で[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。 修正フォームを追加するには、アプリケーション ページを作成し、コードを追加する必要があります。<br />-ワークフローの Elements.xml ファイルをリファクタリングできません。 必要に応じて手動で編集する必要があります。<br />詳細については、次を参照してください[ワークフロー修正フォーム (SharePoint Foundation)。](http://go.microsoft.com/fwlink/?LinkId=187675)|テンプレートはありません。 InfoPath 修正フォームで[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。<br />-がない間の統合[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]および InfoPath デザイナー。<br />-ワークフローの Elements.xml ファイルをリファクタリングできません。|  
  
## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>インポートされた SharePoint 再利用可能なワークフローでのフォームのサポート  
 次の表にリスト[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]にインポートされる SharePoint の再利用可能なワークフローの ASPX または InfoPath のフォーム上のさまざまなフォーム型のサポート[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。  
  
|フォームの種類|SharePoint Designer からインポートされた ASPX 形式を持つ再利用可能なワークフロー|SharePoint Designer からインポートした InfoPath フォームが再利用可能なワークフロー|  
|---------------|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|関連付け|-フォームは、ワークフローの Elements.xml ファイルで参照されています。<br />-ワークフローの Elements.xml ファイルは、フォームの名前を変更または削除すると、ときに、またはその配置パスが変更されたときにリファクターされています。|-フォームは、インポートしますが、ワークフローの Elements.xml で参照されていません。<br />-ワークフローの Elements.xml ファイルをリファクタリングできません。|  
|開始に使用します。|-フォームは、ワークフローの Elements.xml ファイル内のワークフローで参照されます。<br />-ワークフローの Elements.xml ファイルは、フォームの名前を変更または削除すると、ときに、またはその配置パスが変更されたときにリファクターされています。|-フォームは、インポートしますが、ワークフローの Elements.xml で参照されていません。<br />-ワークフローの Elements.xml ファイルをリファクタリングできません。 **注:**ルールとプロパティを追加およびこのシナリオを実現する変更する必要があります。|  
|タスク|-フォームは、ワークフローの Elements.xml ファイルで参照されています。<br />-ワークフローの Elements.xml ファイルをリファクタリングできません。|-フォームは、インポートしますが、ワークフローの Elements.xml で参照されていません。<br />-ワークフローの Elements.xml ファイルをリファクタリングできません。 **注:**ルールとプロパティを追加およびこのシナリオを実現する変更する必要があります。|  
|変更|該当なし。 SharePoint Designer の ASPX の変更のフォームを作成できません。|該当なし。 組み込みの SharePoint サーバーのワークフローは、ワークフローをエクスポートする場合、.wsp ファイルに含まれていないを除く SharePoint デザイナーで変更の InfoPath フォームを作成できません。|  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: アソシエーションと開始フォーム、ワークフローを作成します。](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [SharePoint ワークフロー ソリューションを作成します。](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [既存の SharePoint サイトからの項目のインポート](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  