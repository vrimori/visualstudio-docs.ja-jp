---
title: ソリューション エクスプ ローラーのフィルターを拡張 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf43243abc361df6c5b32b0e71e966c61a501b52
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498789"
---
# <a name="extend-the-solution-explorer-filter"></a>ソリューション エクスプ ローラーのフィルターを拡張します。
拡張する**ソリューション エクスプ ローラー**別のファイルを非表示機能をフィルター処理します。 たとえば、c# クラス ファクトリ内のファイルのみを表示するフィルターを作成することができます、**ソリューション エクスプ ローラー**、このチュートリアルで説明します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)します。  
  
### <a name="create-a-visual-studio-package-project"></a>Visual Studio パッケージ プロジェクトを作成します。  
  
1.  という名前の VSIX プロジェクトを作成する`FileFilter`します。 という名前のカスタム コマンド項目テンプレートを追加**FileFilter**します。 詳細については、次を参照してください。[メニュー コマンドを使用して拡張機能を作成する](../extensibility/creating-an-extension-with-a-menu-command.md)します。  
  
2.  参照を追加`System.ComponentModel.Composition`と`Microsoft.VisualStudio.Utilities`します。  
  
3.  表示されるメニュー コマンド、**ソリューション エクスプ ローラー**ツールバー。 開く、 *FileFilterPackage.vsct*ファイル。  
  
4.  変更、`<Button>`次のブロック。  
  
    ```xml  
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">  
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>FileNameFilter</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
### <a name="update-the-manifest-file"></a>マニフェスト ファイルを更新します。  
  
1.  *Source.extension.vsixmanifest*ファイルを MEF コンポーネントである資産を追加します。  
  
2.  **資産** タブで、選択、**新規**ボタンをクリックします。  
  
3.  **型**フィールドで選択**Microsoft.VisualStudio.MefComponent**します。  
  
4.  **ソース**フィールドで選択**現在のソリューションでプロジェクトを**します。  
  
5.  **プロジェクト**フィールドで選択**FileFilter**、選択し、 **OK**ボタン。  
  
### <a name="add-the-filter-code"></a>フィルターのコードを追加します。  
  
1.  追加するいくつかの Guid、 *FileFilterPackageGuids.cs*ファイル。  
  
    ```csharp  
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file  
    public const int FileFilterId = 0x100;  
    ```  
  
2.  という名前のファイル プロジェクトにクラス ファイルを追加*FileNameFilter.cs*します。  
  
3.  空の名前空間と空のクラスを次のコードに置き換えます。  
  
     `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)`メソッドは、ソリューションのルートを含むコレクションを受け取ります (`rootItems`) し、フィルターに含まれる項目のコレクションを返します。  
  
     `ShouldIncludeInFilter`メソッド内の項目をフィルター処理、**ソリューション エクスプ ローラー**階層が基づくことを条件に指定します。  
  
    ```csharp  
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
  
4.  *FileFilter.cs*FileFilter コンス トラクターからコードを処理、コマンドの配置を削除します。 このよう、結果になります。  
  
    ```csharp  
    private FileFilter(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException("package");  
        }  
  
        this.package = package;  
    }  
    ```  
  
     削除、`ShowMessageBox()`メソッドもします。  
  
5.  *FileFilterPackage.cs*、コードに置き換えます、`Initialize()`を次のメソッド。  
  
    ```csharp  
    protected override void Initialize()  
    {  
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
    }  
    ```  
  
### <a name="test-your-code"></a>コードをテストする  
  
1.  プロジェクトをビルドして実行します。 Visual Studio の 2 番目のインスタンスが表示されます。 これは、実験用インスタンスと呼ばれます。  
  
2.  Visual Studio の実験用インスタンスの c# プロジェクトを開きます。  
  
3.  追加したボタンの表示、**ソリューション エクスプ ローラー**ツールバー。 左から 4 番目のボタンが必要です。  
  
4.  ボタンをクリックすると、すべてのファイル フィルターで除外される必要があります、ことがわかります**ビューからすべての項目がフィルター処理されました。** **ソリューション エクスプ ローラー**します。