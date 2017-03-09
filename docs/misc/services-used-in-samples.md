---
title: "サンプルで使用されているサービス | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "サービス、サンプルに出現"
  - "サンプル、サービス"
ms.assetid: 04864feb-9b8b-45c4-8233-fc2ed9273987
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# サンプルで使用されているサービス
[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] に含まれるサンプルはサービスを利用します。  次のリストはを使用してサンプルといくつかの一般的に使用されるサービスを示します。  
  
> [!NOTE]
>  参照およびサポートされていないサンプルの両方が使用できる場合はサンプル参照だけが表示されます。  
  
|サービス|サンプル|  
|----------|----------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry>|BscEditProjectSubtype|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>|[方法: 動作状況ログの使用](../extensibility/how-to-use-the-activity-log.md)|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsAddProjectItemDlg>|BscPrjFigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject>|BscPrj|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChange>|使用は推奨されていません。  代わりに、<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> を使用してください。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|BscEditFigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>|サンプルの Reference.HelpIntegration。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|サンプルの SingleViewEditor。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors>|サンプルの SingleViewEditor。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|BscPrjFigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceManager>|Reference.PackageReference.ToolWindow多数のサンプル|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|サンプルの SingleViewEditor。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|BscPrjFigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Reference.PackageReference.ToolWindow多数のサンプル|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|BscEdtBscPrjFigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|BscPrjFigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|BscPrjFigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|BscPrjFigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>|SingleViewEditorBscPrjFigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Reference.ToolWindowBscEdit多数のサンプル|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|BscEditFigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWindowFrame>|Reference.ToolWindow|  
  
## 参照  
 [サービスの一覧](../extensibility/internals/list-of-available-services.md)   
 [サービスの基礎](../extensibility/internals/service-essentials.md)