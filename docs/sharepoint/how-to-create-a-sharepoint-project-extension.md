---
title: '方法: SharePoint プロジェクト拡張機能の作成 |Microsoft Docs'
ms.custom: ''
ms.date: 04/28/2017
ms.technology:
- office-development
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
ms.openlocfilehash: 25644a11ddbef3f8d493b64f8ca288dbaa87a14c
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119439"
---
# <a name="how-to-create-a-sharepoint-project-extension"></a>方法: SharePoint プロジェクト拡張機能の作成
  Visual Studio で開いている任意の SharePoint プロジェクトに機能を追加する場合は、プロジェクトの拡張機能を作成します。 詳細については、次を参照してください。 [SharePoint プロジェクト システムを拡張](../sharepoint/extending-the-sharepoint-project-system.md)します。  

### <a name="to-create-a-project-extension"></a>プロジェクトの拡張機能を作成するには  

1.  クラス ライブラリ プロジェクトを作成します。  

2.  次のアセンブリへの参照を追加します。  

    -   Microsoft.VisualStudio.SharePoint  

    -   System.ComponentModel.Composition  

3.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> インターフェイスを実装するクラスを作成します。  

4.  追加、<xref:System.ComponentModel.Composition.ExportAttribute>クラスにします。 この属性により、Visual Studio を検出して読み込む、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>実装します。 渡す、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>属性コンス トラクターの型。  

5.  実装で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>メソッドのメンバーを使用して、 *projectService*パラメーター、拡張機能の動作を定義します。 このパラメーターは、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>で定義されたイベントへのアクセスを提供するオブジェクト、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents>インターフェイス。  

## <a name="example"></a>例  
 次のコード例で定義されている SharePoint プロジェクト イベントのほとんどを処理する単純なプロジェクトの拡張機能を作成する方法を示します、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents>インターフェイス。 SharePoint プロジェクトを作成するコードをテストするには、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]とし、その他のプロジェクトをソリューションに追加、プロジェクト プロパティの値を変更または削除またはプロジェクトを除外します。 メッセージを記述することで、拡張機能を通知するイベントの**出力**ウィンドウと**エラー一覧**ウィンドウ。  

  ```vb  
    Imports Microsoft.VisualStudio.SharePoint
    Imports System.ComponentModel
    Imports System.ComponentModel.Composition

    Namespace Contoso.ExampleProjectExtension
      <Export(GetType(ISharePointProjectExtension))> _
      Class ExampleProjectExtension
        Implements ISharePointProjectExtension

        Private WithEvents projectService As ISharePointProjectService

        Public Sub Initialize(ByVal projectService As ISharePointProjectService) _
            Implements ISharePointProjectExtension.Initialize
            Me.projectService = projectService
        End Sub

        ' A project was added.
        Private Sub projectService_ProjectAdded(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectAdded
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project was added: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project was loaded in the IDE.
        Private Sub projectService_ProjectInitialized(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectInitialized
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project is being initialized: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' The name of a property was changed.
        Private Sub projectService_ProjectNameChanged(ByVal sender As Object, ByVal e As NameChangedEventArgs) _
            Handles projectService.ProjectNameChanged
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The project named {0} was changed to {1}.", e.OldName, project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project property value was changed.
        Private Sub ProjectPropertyChanged(ByVal sender As Object, ByVal e As PropertyChangedEventArgs) _
            Handles projectService.ProjectPropertyChanged
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following property of the {0} project was changed: {1}",
                project.Name, e.PropertyName)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project is being removed or unloaded.
        Private Sub projectService_ProjectRemoved(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectRemoved
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project is being removed or unloaded: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project was removed or unloaded.
        Private Sub projectService_ProjectDisposing(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectDisposing
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project was removed or unloaded: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub
      End Class
    End Namespace  
    ```  

    ```csharp  
    using Microsoft.VisualStudio.SharePoint;
    using System;
    using System.ComponentModel;
    using System.ComponentModel.Composition;

    namespace Contoso.ExampleProjectExtension
    {
      [Export(typeof(ISharePointProjectExtension))]
      internal class ExampleProjectExtension : ISharePointProjectExtension
      {
        public void Initialize(ISharePointProjectService projectService)
        {
            projectService.ProjectAdded += projectService_ProjectAdded;
            projectService.ProjectInitialized += projectService_ProjectInitialized;
            projectService.ProjectNameChanged += projectService_ProjectNameChanged;
            projectService.ProjectPropertyChanged += projectService_ProjectPropertyChanged;
            projectService.ProjectRemoved += projectService_ProjectRemoved;
            projectService.ProjectDisposing += projectService_ProjectDisposing;
        }

        // A project was added.
        void projectService_ProjectAdded(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project was added: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project is loaded in the IDE.
        void projectService_ProjectInitialized(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project is being initialized: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // The name of a project was changed.
        void projectService_ProjectNameChanged(object sender, NameChangedEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The project named {0} was changed to {1}.", e.OldName, project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project property value was changed.
        private void projectService_ProjectPropertyChanged(object sender, PropertyChangedEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following property of the {0} project was changed: {1}",
                project.Name, e.PropertyName);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project is being removed or unloaded.
        void projectService_ProjectRemoved(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project is being removed or unloaded: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project was removed or unloaded.
        void projectService_ProjectDisposing(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project was removed or unloaded: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }
     }
  }  
  ```  

この例では、SharePoint プロジェクト サービスを使用して、メッセージを書き込む、**出力**ウィンドウと**エラー一覧**ウィンドウ。 詳細については、次を参照してください。 [SharePoint プロジェクト サービスを使用して、](../sharepoint/using-the-sharepoint-project-service.md)します。  

 処理する方法を示す例について、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested>と<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>イベントを参照してください[方法: ショートカット メニュー項目を SharePoint プロジェクトに追加](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)と[方法: SharePoint プロジェクトにプロパティを追加](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  

## <a name="compile-the-code"></a>コードをコンパイルします  
 この例では、次のアセンブリへの参照が必要です。  

-   Microsoft.VisualStudio.SharePoint  

-   System.ComponentModel.Composition  

## <a name="deploy-the-extension"></a>拡張機能をデプロイします。  
 拡張機能を展開するには、作成、[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [、SharePoint 用の拡張機能の展開ツールの Visual Studio で](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)します。  

## <a name="see-also"></a>関連項目
 [SharePoint プロジェクト システムを拡張します。](../sharepoint/extending-the-sharepoint-project-system.md)   
 [方法: SharePoint プロジェクトのショートカット メニュー項目の追加](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [方法: SharePoint プロジェクトにプロパティを追加](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [チュートリアル: SharePoint プロジェクト拡張機能を作成します。](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)  
