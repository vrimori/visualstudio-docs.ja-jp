---
title: "ソリューション エクスプ ローラーのフィルターを拡張します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ソリューション エクスプ ローラーを拡張します。"
  - "プロジェクトおよびソリューションの機能拡張 [Visual Studio]"
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# ソリューション エクスプ ローラーのフィルターを拡張します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

拡張する **ソリューション エクスプ ローラー** と別のファイルを非表示機能をフィルター処理します。 たとえば、c\# クラス ファクトリ内のファイルのみを表示するフィルターを作成することができます、 **ソリューション エクスプ ローラー**, についても説明してください。  
  
## 必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
### Visual Studio パッケージ プロジェクトを作成します。  
  
1.  という名前の VSIX プロジェクトを作成する `FileFilter`です。 という名前のカスタム コマンド項目テンプレートを追加 **FileFilter**します。 詳細については、「[メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)」を参照してください。  
  
2.  参照を追加 `System.ComponentModel.Composition` と `Microsoft.VisualStudio.Utilities`です。  
  
3.  表示されるメニュー コマンド、 **ソリューション エクスプ ローラー** ツールバーです。 FileFilterPackage.vsct ファイルを開きます。  
  
4.  変更、 `<Button>` には、次のブロック。  
  
    ```xml  
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">  
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>FileNameFilter</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
### マニフェスト ファイルを更新します。  
  
1.  Source.extension.vsixmanifest ファイルでは、MEF コンポーネントである資産を追加します。  
  
2.  **\[アセット\]** タブで **\[新規作成\]** をクリックします。  
  
3.  **型** フィールドで、選択 **Microsoft.VisualStudio.MefComponent**します。  
  
4.  **ソース** フィールドで、選択 **現在のソリューション内のプロジェクト**します。  
  
5.  **プロジェクト** フィールドで、選択 **FileFilter**, を選択し、 **OK** \] ボタンをクリックします。  
  
### フィルターのコードを追加します。  
  
1.  いくつかの Guid を FileFilterPackageGuids.cs ファイルに追加します。  
  
    ```c#  
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file  
    public const int FileFilterId = 0x100;  
    ```  
  
2.  FileNameFilter.cs をという名前のファイル プロジェクトにクラス ファイルを追加します。  
  
3.  空の名前空間と空のクラスを次のコードに置き換えます。  
  
     `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` メソッドは、ソリューションのルートを含むコレクションを受け取ります \(`rootItems`\) し、フィルターに含まれる項目のコレクションを返します。  
  
     `ShouldIncludeInFilter` メソッド内の項目をフィルター処理、 **ソリューション エクスプ ローラー** を指定するという条件に基づく階層です。  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Text.RegularExpressions;  
    using System.Threading.Tasks;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio.Shell;  
  
    namespace FileFilter  
    {  
        // Implements ISolutionTreeFilterProvider. The SolutionTreeFilterProvider attribute declares it as a MEF component  
        [SolutionTreeFilterProvider(FileFilterPackageGuids.guidFileFilterPackageCmdSetString, (uint)(FileFilterPackageGuids.FileFilterId))]  
        public sealed class FileNameFilterProvider : HierarchyTreeFilterProvider  
        {  
            SVsServiceProvider svcProvider;  
            IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;  
  
            // Constructor required for MEF composition  
            [ImportingConstructor]  
            public FileNameFilterProvider(SVsServiceProvider serviceProvider, IVsHierarchyItemCollectionProvider hierarchyCollectionProvider)  
            {  
                this.svcProvider = serviceProvider;  
                this.hierarchyCollectionProvider = hierarchyCollectionProvider;  
            }  
  
            // Returns an instance of Create filter class.  
            protected override HierarchyTreeFilter CreateFilter()  
            {  
                return new FileNameFilter(this.svcProvider, this.hierarchyCollectionProvider, FileNamePattern);  
            }  
  
            // Regex pattern for CSharp factory classes  
            private const string FileNamePattern = @"\w*factory\w*(.cs$)";  
  
            // Implementation of file filtering  
            private sealed class FileNameFilter : HierarchyTreeFilter  
            {  
                private readonly Regex regexp;  
                private readonly IServiceProvider svcProvider;  
                private readonly IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;  
  
                public FileNameFilter(  
                    IServiceProvider serviceProvider,  
                    IVsHierarchyItemCollectionProvider hierarchyCollectionProvider,  
                    string fileNamePattern)  
                {  
                    this.svcProvider = serviceProvider;  
                    this.hierarchyCollectionProvider = hierarchyCollectionProvider;  
                    this.regexp = new Regex(fileNamePattern, RegexOptions.IgnoreCase);  
                }  
  
                // Gets the items to be included from this filter provider.   
                // rootItems is a collection that contains the root of your solution  
                // Returns a collection of items to be included as part of the filter  
                protected override async Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem> rootItems)  
                {  
                    IVsHierarchyItem root = HierarchyUtilities.FindCommonAncestor(rootItems);  
                    IReadOnlyObservableSet<IVsHierarchyItem> sourceItems;  
                    sourceItems = await hierarchyCollectionProvider.GetDescendantsAsync(  
                                        root.HierarchyIdentity.NestedHierarchy,  
                                        CancellationToken);  
  
                    IFilteredHierarchyItemSet includedItems = await hierarchyCollectionProvider.GetFilteredHierarchyItemsAsync(  
                        sourceItems,  
                        ShouldIncludeInFilter,  
                        CancellationToken);  
                    return includedItems;  
                }  
  
                // Returns true if filters hierarchy item name for given filter; otherwise, false</returns>  
                private bool ShouldIncludeInFilter(IVsHierarchyItem hierarchyItem)  
                {  
                    if (hierarchyItem == null)  
                    {  
                        return false;  
                    }  
                    return this.regexp.IsMatch(hierarchyItem.Text);  
                }  
            }  
        }  
    }  
  
    ```  
  
4.  FileFilter.cs では、FileFilter コンス トラクターからコマンドの配置と処理のコードを削除します。 結果は、次のようになります。  
  
    ```c#  
    private FileFilter(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException("package");  
        }  
  
        this.package = package;  
    }  
    ```  
  
     ShowMessageBox\(\) メソッドを削除します。  
  
5.  FileFilterPackage、cs では、次のように Initialize\(\) メソッドのコードを置き換えます。  
  
    ```c#  
    protected override void Initialize()  
    {  
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
    }  
    ```  
  
### コードをテストします。  
  
1.  プロジェクトをビルドして実行します。 Visual Studio の 2 つ目のインスタンスが表示されます。 これは、実験用インスタンスと呼ばれます。  
  
2.  Visual Studio の実験用インスタンスでは、c\# プロジェクトを開きます。  
  
3.  ソリューション エクスプ ローラーのツールバーに追加したボタンを探します。 左から 4 番目のボタンができます。  
  
4.  ボタンをクリックすると、すべてのファイルをフィルター処理する必要があり、「すべての項目がフィルター選択されたビューからです」が表示されます。 ソリューション エクスプ ローラー。