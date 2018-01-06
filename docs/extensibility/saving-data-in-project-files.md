---
title: "プロジェクト ファイル内のデータ保存 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 42273797b1010afdee3d317e7aa2e6ae4362a7bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="saving-data-in-project-files"></a>プロジェクト ファイル内のデータを保存
プロジェクトのサブタイプでは、保存でき、プロジェクト ファイル内のサブタイプに固有のデータを取得することができます。 Managed Package Framework (MPF) は、このタスクを実行する 2 つのインターフェイスを提供します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>からアクセス プロパティの値により、インターフェイス、 **MSBuild**プロジェクト ファイルのセクションです。 によって提供されるメソッド<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>読み込みまたは保存にユーザーのニーズが関連するデータをビルドするたびにすべてのユーザーが呼び出すことができます。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>自由形式の XML でないビルド関連のデータを保持するために使用します。 によって提供されるメソッド<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>によって呼び出される[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]されるたびに[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]プロジェクト ファイルでないビルド関連のデータを保持する必要があります。  
  
 ビルドと非ビルド関連のデータを維持する方法の詳細については、次を参照してください。 [MSBuild プロジェクト ファイル内のデータの永続化](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)です。  
  
## <a name="saving-and-retrieving-build-related-data"></a>関連するデータの保存およびビルドを取得します。  
  
#### <a name="to-save-a-build-related-data-in-the-project-file"></a>関連するプロジェクト ファイルでデータを保存、ビルド  
  
-   呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A>プロジェクト ファイルの完全なパスを保存するメソッド。  
  
    ```  
    private SpecializedProject project;  
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;  
    string newFullPath = GetNewFullPath();  
    // Set a full path of the project file.  
    ErrorHandler.ThrowOnFailure(projectStorage.SetPropertyValue(  
        "MSBuildProjectDirectory",  
        String.Empty,  
        (uint)_PersistStorageType.PST_PROJECT_FILE, newFullPath));  
    ```  
  
#### <a name="to-retrieve-build-related-data-from-the-project-file"></a>関連するデータをプロジェクト ファイルからビルドを取得するには  
  
-   呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A>プロジェクト ファイルの完全なパスを取得します。  
  
    ```  
    private SpecializedProject project;  
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;  
    string fullPath;  
    // Get a full path of the project file.  
    ErrorHandler.ThrowOnFailure(projectStorage.GetPropertyValue(  
        "MSBuildProjectDirectory",  
        String.Empty,  
        (uint)_PersistStorageType.PST_PROJECT_FILE, out fullPath));  
    ```  
  
## <a name="saving-and-retrieving-non-build-related-data"></a>保存と取得以外のビルド関連データ  
  
#### <a name="to-save-non-build-related-data-in-the-project-file"></a>保存のないビルドに関連するプロジェクト ファイル内のデータ  
  
1.  実装、<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A>が最後に、XML フラグメントが変更されたかどうかを決定するメソッドが現在のファイルを保存します。  
  
    ```  
    public int IsFragmentDirty(uint storage, out int pfDirty)  
    {  
        pfDirty = 0;  
        switch (storage)  
        {  
            case (uint)_PersistStorageType.PST_PROJECT_FILE:  
            {  
                if (isDirty)  
                    pfDirty |= 1;  
                break;  
            }  
            case (uint)_PersistStorageType.PST_USER_FILE:  
            {  
                // We do not store anything in the user file.  
                break;  
            }  
        }  
  
        // Forward the call to inner flavor(s)   
        if (pfDirty == 0 && innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).IsFragmentDirty(storage, out pfDirty);  
  
        return VSConstants.S_OK;  
  
    }  
    ```  
  
2.  実装、<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A>メソッドをプロジェクト ファイルに XML データを保存します。  
  
    ```  
    public int Save(ref Guid guidFlavor, uint storage, out string pbstrXMLFragment, int fClearDirty)  
    {  
        pbstrXMLFragment = null;  
  
        if (IsMyFlavorGuid(ref guidFlavor))  
        {  
            switch (storage)  
            {  
                case (uint)_PersistStorageType.PST_PROJECT_FILE:  
                {  
                    // Create XML for our data.  
                    XmlDocument doc = new XmlDocument();  
                    XmlNode root = doc.CreateElement(this.GetType().Name);  
  
                    XmlNode node = doc.CreateElement(targetsTag);  
                    node.AppendChild(doc.CreateTextNode(this.TargetsToExecute));  
                    root.AppendChild(node);  
  
                    node = doc.CreateElement(updateTargetsTag);  
                    node.AppendChild(doc.CreateTextNode(this.UpdateTargetList.ToString()));  
                    root.AppendChild(node);  
  
                    doc.AppendChild(root);  
                    // Get XML fragment representing our data  
                    pbstrXMLFragment = doc.InnerXml;  
  
                    if (fClearDirty != 0)  
                        isDirty = false;  
                    break;  
                }  
                case (uint)_PersistStorageType.PST_USER_FILE:  
                {  
                    // We do not store anything in the user file.  
                    break;  
                }  
            }  
        }  
  
        // Forward the call to inner flavor(s)  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).Save(ref guidFlavor, storage, out pbstrXMLFragment, fClearDirty);  
  
        return VSConstants.S_OK;  
    }  
    ```  
  
#### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>プロジェクト ファイルでないビルド関連のデータを取得するには  
  
1.  実装、<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A>プロジェクト拡張機能プロパティおよびその他のビルドに依存しないデータを初期化します。 このメソッドは、XML 構成内のデータがプロジェクト ファイルがない場合に呼び出されます。  
  
    ```  
    public int InitNew(ref Guid guidFlavor, uint storage)  
    {  
        //Return,if it is our guid.  
        if (IsMyFlavorGuid(ref guidFlavor))  
            return VSConstants.S_OK;  
  
        //Forward the call to inner flavor(s).  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).InitNew(ref guidFlavor, storage);  
  
        return VSConstants.S_OK;  
    ```  
  
2.  実装、<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A>プロジェクト ファイルから XML データを読み込みます。  
  
    ```  
    public int Load(ref Guid guidFlavor, uint storage, string pszXMLFragment)  
    {  
        if (IsMyFlavorGuid(ref guidFlavor))  
        {  
            switch (storage)  
            {  
                case (uint)_PersistStorageType.PST_PROJECT_FILE:  
                {  
                    // Load our data from the XML fragment.  
                    XmlDocument doc = new XmlDocument();  
                    XmlNode node = doc.CreateElement(this.GetType().Name);  
                    node.InnerXml = pszXMLFragment;  
                    if (node == null  
                        || node.FirstChild == null  
                        || node.FirstChild.ChildNodes.Count == 0  
                        || node.FirstChild.ChildNodes[0].Name != targetsTag)  
                        break;  
                    this.TargetsToExecute = node.FirstChild.ChildNodes[0].InnerText;  
  
                    if (node.FirstChild.ChildNodes.Count <= 1  
                        || node.FirstChild.ChildNodes[1].Name != updateTargetsTag)  
                        break;  
                    this.UpdateTargetList = bool.Parse(node.FirstChild.ChildNodes[1].InnerText);  
                    break;  
                }  
                case (uint)_PersistStorageType.PST_USER_FILE:  
                {  
                    // We do not store anything in the user file.  
                    break;  
                }  
            }  
        }  
  
        // Forward the call to inner flavor(s)  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).Load(ref guidFlavor, storage, pszXMLFragment);  
  
        return VSConstants.S_OK;  
    }  
    ```  
  
> [!NOTE]
>  このトピックで提供されるすべてのコード例は例での部分[VSSDK のサンプル](http://aka.ms/vs2015sdksamples)です。  
  
## <a name="see-also"></a>参照  
 [MSBuild プロジェクト ファイルでのデータの保持](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)