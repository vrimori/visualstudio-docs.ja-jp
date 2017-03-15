---
title: "プロジェクト項目のプロパティを永続化します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクト項目に追加のプロパティ"
  - "プロパティを追加するプロジェクト項目"
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# プロジェクト項目のプロパティを永続化します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ソース ファイルの作成者などのプロジェクト項目に追加するプロパティを永続化することがあります。 プロジェクト ファイルで、プロパティを格納することで、これを行うことができます。  
  
 プロジェクト ファイルのプロパティを永続化する最初の手順は、プロジェクトの階層を取得する、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> インターフェイスです。 オートメーションを使用して、またはを使用して、このインターフェイスを取得できる <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>です。 インターフェイスを取得した後に使用するにをプロジェクト項目が現在選択されているかを判断します。 プロジェクト項目の ID を作成したら、使用できます <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> プロパティを追加します。  
  
 VsPkg.cs プロパティを永続化する次の手順で `Author` 値を持つ `Tom` プロジェクト ファイルにします。  
  
### DTE オブジェクトを含むプロジェクトの階層を取得するには  
  
1.  次のコードを VSPackage に追加します。  
  
    ```c#  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE)); EnvDTE.Project project = dte.Solution.Projects.Item(1); string uniqueName = project.UniqueName; IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution)); IVsHierarchy hierarchy; solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    ```  
  
### DTE オブジェクトとプロジェクト項目のプロパティを永続化するには  
  
1.  前の手順で、メソッドで指定されたコードに次のコードを追加します。  
  
    ```c#  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage; if (buildPropertyStorage != null) { uint itemId; string fullPath = (string)project.ProjectItems.Item( "VsPkg.cs").Properties.Item("FullPath").Value; hierarchy.ParseCanonicalName(fullPath, out itemId); buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom"); }  
    ```  
  
### IVsMonitorSelection を使用して、プロジェクト階層を取得するには  
  
1.  次のコードを VSPackage に追加します。  
  
    ```c#  
    IVsHierarchy hierarchy = null; IntPtr hierarchyPtr = IntPtr.Zero; IntPtr selectionContainer = IntPtr.Zero; uint itemid; // Retrieve shell interface in order to get current selection IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection; if (monitorSelection == null) throw new InvalidOperationException(); try { // Get the current project hierarchy, project item, and selection container for the current selection // If the selection spans multiple hierachies, hierarchyPtr is Zero IVsMultiItemSelect multiItemSelect = null; ErrorHandler.ThrowOnFailure( monitorSelection.GetCurrentSelection( out hierarchyPtr, out itemid, out multiItemSelect, out selectionContainer)); // We only care if there is only one node selected in the tree if (!(itemid == VSConstants.VSITEMID_NIL || hierarchyPtr == IntPtr.Zero || multiItemSelect != null || itemid == VSConstants.VSITEMID_SELECTION)) { hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr) as IVsHierarchy; } } finally { if (hierarchyPtr != IntPtr.Zero) Marshal.Release(hierarchyPtr); if (selectionContainer != IntPtr.Zero) Marshal.Release(selectionContainer); }  
    ```  
  
2.  
  
### 選択したプロジェクト項目のプロパティを永続化プロジェクトの階層構造を指定するには  
  
1.  前の手順で、メソッドで指定されたコードに次のコードを追加します。  
  
    ```  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage; if (buildPropertyStorage != null) { buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom"); }  
    ```  
  
### プロパティが保存されていることを確認するには  
  
1.  開始 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 開くか、ソリューションを作成します。  
  
2.  プロジェクトを選択項目で VsPkg.cs **ソリューション エクスプ ローラー**します。  
  
3.  ブレークポイントを使用して、またはそれ以外の場合、VSPackage が読み込まれ、SetItemAttribute が実行されることを確認します。  
  
    > [!NOTE]
    >  Autoload UI において、VSPackage を作成することができます <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists>します。 詳細については、「[Vspackage を読み込む](../extensibility/loading-vspackages.md)」を参照してください。  
  
4.  閉じる [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] メモ帳で、プロジェクト ファイルを開きます。 Tom の値を持つ \< Author \> タグは次のように表示されます。  
  
    ```  
    <Compile Include="VsPkg.cs"> <Author>Tom</Author> </Compile>  
    ```  
  
## 参照  
 [カスタム ツール](../extensibility/internals/custom-tools.md)