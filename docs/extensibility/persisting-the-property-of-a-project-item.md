---
title: プロジェクト項目のプロパティを永続化 |Microsoft ドキュメント
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6f569a8fe57a215a4fcce31de53c8c4a59f51177
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="persisting-the-property-of-a-project-item"></a>プロジェクト項目のプロパティを永続化します。
ソース ファイルの作成者などのプロジェクト アイテムを追加するプロパティを永続化することがあります。 プロジェクト ファイルでプロパティを格納することで、これを行うことができます。

 プロジェクト ファイルのプロパティを永続化する最初の手順は、プロジェクトの階層を取得する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>インターフェイスです。 このインターフェイスを取得するには、オートメーションを使用して、またはを使用して<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>です。 インターフェイスを取得した後は、現在選択されているプロジェクト項目を使用できます。 使用することができます、プロジェクト項目の ID を作成したら、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A>プロパティを追加します。

 VsPkg.cs プロパティを永続化する次の手順で`Author`値を持つ`Tom`プロジェクト ファイルにします。

### <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>DTE オブジェクトをプロジェクトの階層を取得するには

1.  VSPackage に次のコードを追加します。

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

### <a name="to-persist-the-project-item-property-with-the-dte-object"></a>DTE オブジェクトをプロジェクト項目のプロパティを永続化するには

1.  前の手順で、メソッドで指定されたコードに次のコードを追加します。

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item(
            "VsPkg.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

### <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>IVsMonitorSelection を使用して、プロジェクト階層を取得するには

1.  VSPackage に次のコードを追加します。

    ```csharp
    IVsHierarchy hierarchy = null;
    IntPtr hierarchyPtr = IntPtr.Zero;
    IntPtr selectionContainer = IntPtr.Zero;
    uint itemid;

    // Retrieve shell interface in order to get current selection
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;
    if (monitorSelection == null)
        throw new InvalidOperationException();

    try
    {
        // Get the current project hierarchy, project item, and selection container for the current selection
        // If the selection spans multiple hierachies, hierarchyPtr is Zero
        IVsMultiItemSelect multiItemSelect = null;
        ErrorHandler.ThrowOnFailure(
            monitorSelection.GetCurrentSelection(
                out hierarchyPtr, out itemid,
                out multiItemSelect, out selectionContainer));

        // We only care if there is only one node selected in the tree
        if (!(itemid == VSConstants.VSITEMID_NIL ||
            hierarchyPtr == IntPtr.Zero ||
            multiItemSelect != null ||
            itemid == VSConstants.VSITEMID_SELECTION))
        {
            hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr)
                as IVsHierarchy;
        }
    }
    finally
    {
        if (hierarchyPtr != IntPtr.Zero)
            Marshal.Release(hierarchyPtr);
        if (selectionContainer != IntPtr.Zero)
            Marshal.Release(selectionContainer);
    }
    ```

2.

### <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>プロジェクトの階層を指定された選択したプロジェクト項目のプロパティを永続化するには

1.  前の手順で、メソッドで指定されたコードに次のコードを追加します。

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

### <a name="to-verify-that-the-property-is-persisted"></a>プロパティが保存されることを確認するには

1.  開始[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]開くか、ソリューションを作成します。

2.  プロジェクトを選択項目で VsPkg.cs**ソリューション エクスプ ローラー**です。

3.  ブレークポイントを使用してまたはそれ以外の場合、VSPackage が読み込まれ、SetItemAttribute が実行されています。

    > [!NOTE]
    > Autoload UI コンテキストで VSPackage を作成することができます<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>です。 詳細については、次を参照してください。[読み込み Vspackage](../extensibility/loading-vspackages.md)です。

4.  閉じる[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]し、メモ帳で、プロジェクト ファイルを開きます。 表示されます、\<作成者 > Tom、値を持つタグを次のようにします。

    ```xml
    <Compile Include="VsPkg.cs">
        <Author>Tom</Author>
    </Compile>
    ```

## <a name="see-also"></a>関連項目

- [カスタム ツール](../extensibility/internals/custom-tools.md)