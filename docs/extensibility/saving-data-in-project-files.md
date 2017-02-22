---
title: "プロジェクト ファイル内のデータを保存 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "データ [Visual Studio] のプロジェクト ファイルの保存"
  - "プロジェクト ファイル"
  - "プロジェクト ファイル、データの保存"
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
caps.latest.revision: 28
caps.handback.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
---
# プロジェクト ファイル内のデータを保存
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

プロジェクトのサブタイプはプロジェクト ファイルの各サブタイプに固有のデータを格納および取得できます。  マネージ パッケージ フレームワークはこの \(MPF\) タスクを実行するための 2 種類のインターフェイスが用意されています :  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> のインターフェイスはプロジェクト ファイルの **MSBuild** のセクションのプロパティ値にアクセスできます。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> によって提供されるメソッドはユーザーによってビルド関連のデータの読み込みまたは保存するとユーザーのニーズといつでも呼び出すことができます。  
  
-   自由な書式の XML ではビルドの保持するために <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 関連データが使用されます。  <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> によって提供されるメソッドは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] によってたびにプロジェクト ファイルでビルドの保持する必要 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の関連データ呼び出されます。  
  
 方法の詳細については関連データがビルドと非ビルドの保持する[MSBuild プロジェクト ファイルでデータを保持します。](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md) が表示されます。  
  
## ビルドの関連データを保存および取得します。  
  
#### プロジェクト ファイルのビルドに関連データを保存するには  
  
-   プロジェクト ファイルの完全なパスを格納する <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> のメソッドを呼び出します。  
  
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
  
#### ビルド関連のデータをプロジェクト ファイルから取得するには  
  
-   プロジェクト ファイルの完全なパスを取得するに <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> のメソッドを呼び出します。  
  
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
  
## 非ビルドに関連データを保存および取得します。  
  
#### プロジェクト ファイルでビルドの関連データを保存します。  
  
1.  現在のファイルに最後に保存されてから XML フラグメントが変更されたかどうかを判断するに <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> のメソッドを実装します。  
  
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
  
2.  プロジェクト ファイル内の XML データを保存するに <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> のメソッドを実装します。  
  
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
  
#### プロジェクト ファイルでビルドの関連データを取得します。  
  
1.  プロジェクトの拡張機能のプロパティおよびそのほかのビルドに依存しないデータを初期化するために <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> のメソッドを実装します。  このメソッドはプロジェクト ファイルに現在の XML 構成データがない場合に呼び出されます。  
  
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
  
2.  プロジェクト ファイルの XML データを読み込むに <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> のメソッドを実装します。  
  
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
>  このトピックで説明するすべてのコード例はより大きな例の一部 [VSSDK のサンプル](../misc/vssdk-samples.md)です。  
  
## 参照  
 [MSBuild プロジェクト ファイルでデータを保持します。](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)