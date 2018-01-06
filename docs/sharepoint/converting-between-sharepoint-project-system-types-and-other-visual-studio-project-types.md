---
title: "SharePoint プロジェクト システムの種類とその他の Visual Studio プロジェクトの種類間の変換 |Microsoft ドキュメント"
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
helpviewer_keywords: SharePoint project service
ms.assetid: ad5d8ab2-1659-4e6a-8783-47e0dad44b11
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 81573598dc4c23f161298aee800b5dfabe7608f7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>SharePoint プロジェクト システムと他の Visual Studio プロジェクトの間の型変換
  場合によっては、SharePoint プロジェクト システムでオブジェクトがある可能性があり、Visual Studio オートメーション オブジェクト モデルまたは統合オブジェクト モデル内の対応するオブジェクトの機能を使用する場合またはその逆です。 このような場合は、使用することができます、 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> SharePoint プロジェクト サービスのオブジェクトを別のオブジェクト モデルに変換するメソッド。  
  
 たとえば、する必要があります、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>のみで使用できるメソッドを使用するオブジェクトが、<xref:EnvDTE.Project>または<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>オブジェクト。 この場合、使用することができます、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A>に変換する方法、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>を<xref:EnvDTE.Project>または<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>です。  
  
 Visual Studio オートメーション オブジェクト モデルと Visual Studio の統合オブジェクト モデルの詳細については、次を参照してください。[プログラミング モデルの SharePoint ツール拡張機能の概要](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)です。  
  
## <a name="types-of-conversions"></a>型の変換  
 次の表には、このメソッドは、SharePoint プロジェクト システムと他の Visual Studio のオブジェクト モデルの間で変換できる型が一覧表示します。  
  
|SharePoint プロジェクト システムの種類|オートメーションとの統合オブジェクト モデルで対応する型|  
|------------------------------------|-------------------------------------------------------------------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> または<br /><br /> プロジェクトの基になる COM オブジェクトによって実装されている Visual Studio の統合オブジェクト モデル内の任意のインターフェイス これらのインターフェイスを含める<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (または派生インターフェイス)、および<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>です。 プロジェクトによって実装される主なインターフェイスの一覧は、次を参照してください。[プロジェクト モデルのコア コンポーネント](/visualstudio/extensibility/internals/project-model-core-components)です。|  
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> または<br /><br /> A<xref:System.UInt32> (、VSITEMID とも呼ばれます) に含まれるプロジェクトのメンバーを識別する値、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>含まれています。 この値に渡されることができます、 *itemid*いくつかのパラメーター<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>メソッドです。|  
  
## <a name="example"></a>例  
 次のコード例を使用する方法を示しています、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A>に変換する方法、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>オブジェクトを<xref:EnvDTE.Project>です。  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]  
  
 この例で必要な要素は次のとおりです。  
  
-   EnvDTE.dll アセンブリへの参照を含む SharePoint プロジェクト システムの拡張機能です。 詳細については、次を参照してください。 [SharePoint プロジェクト システムを拡張する](../sharepoint/extending-the-sharepoint-project-system.md)です。  
  
-   登録するコード、`projectService_ProjectAdded`を処理するメソッド、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded>のイベント、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>オブジェクト。 例については、次を参照してください。[する方法: SharePoint プロジェクトの拡張機能を作成する](../sharepoint/how-to-create-a-sharepoint-project-extension.md)です。  
  
## <a name="see-also"></a>参照  
 [SharePoint プロジェクト サービスの使用](../sharepoint/using-the-sharepoint-project-service.md)   
 [方法: SharePoint プロジェクト サービスの取得](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [SharePoint ツール拡張機能のプログラミング モデルの概要](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  