---
title: ".NET Framework 4 または .NET Framework 4.5 に移行する Outlook プロジェクトのフォーム領域の更新 |Microsoft ドキュメント"
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
helpviewer_keywords: Office projects [Office development in Visual Studio], migrating to .NET Framework 4
ms.assetid: 65991e2f-4875-49f0-b21b-6a3d0175d0f4
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 44489e710de11357b68ad4312b0c2460f26f1fe6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="updating-form-regions-in-outlook-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>.NET Framework 4 または .NET Framework 4.5 に移行する Outlook プロジェクトのフォーム領域の更新
  フォーム領域を含む Outlook VSTO アドイン プロジェクトのターゲット フレームワークを [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更する場合は、生成されるフォーム領域コードおよび実行時に特定のフォーム領域クラスをインスタンス化するすべてのコードに対して、いくつかの変更を加える必要があります。  
  
## <a name="updating-the-generated-form-region-code"></a>生成されたフォーム領域コードの更新  
 プロジェクトのターゲット フレームワークが [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更される場合は、生成されるフォーム領域コードを変更する必要があります。 加える変更は、Visual Studio でデザインしたフォーム領域と、Outlook からインポートしたフォーム領域とで異なります。 これらのフォーム領域の種類の違いの詳細については、「 [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md)」を参照してください。  
  
#### <a name="to-update-the-generated-code-for-a-form-region-that-you-designed-in-visual-studio"></a>Visual Studio でデザインしたフォーム領域の生成されたコードを更新するには  
  
1.  コード エディターでフォーム領域の分離コード ファイルを開きます。 このファイル名は *YourFormRegion*.Designer.cs または *YourFormRegion*.Designer.vb です。 Visual Basic プロジェクトでこのファイルを確認するには、 **ソリューション エクスプローラー** の **[すべてのファイルの表示]**ボタンをクリックします。  
  
2.  派生するように、フォーム領域クラスの宣言を変更<xref:Microsoft.Office.Tools.Outlook.FormRegionBase>Microsoft.Office.Tools.Outlook.FormRegionControl の代わりにします。  
  
3.  次のコード例に示すように、フォーム領域クラスのコンストラクターを変更します。  
  
     .NET Framework 3.5 を対象とするプロジェクトのフォーム領域クラスのコンストラクターを、次のコード例に示します。  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(formRegion)  
        Me.InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(formRegion)  
    {  
        this.InitializeComponent();  
    }  
    ```  
  
     [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]を対象とするプロジェクトのフォーム領域クラスのコンストラクターを、次のコード例に示します。  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(Globals.Factory, formRegion)  
        Me.InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(Globals.Factory, formRegion)  
    {  
        this.InitializeComponent();  
    }  
    ```  
  
4.  次に示すように、 `InitializeManifest` メソッドのシグネチャを変更します。 メソッドのコードを変更していないことを確認します。このコードは、デザイナーで適用したフォーム領域の設定を表します。 Visual C# プロジェクトの場合、このメソッドを表示するには、 `Form Region Designer generated code` という名前の領域を展開する必要があります。  
  
     .NET Framework 3.5 を対象とするプロジェクトの `InitializeManifest` メソッドのシグネチャを次のコード例に示します。  
  
    ```vb  
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest)  
  
        ' Do not change code in this method.  
    End Sub  
    ```  
  
    ```csharp  
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest)  
    {  
        // Do not change code in this method.  
    }  
    ```  
  
     `InitializeManifest` を対象とするプロジェクトの [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]メソッドのシグネチャを次のコード例に示します。  
  
    ```vb  
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest,   
        ByVal factory As Microsoft.Office.Tools.Outlook.Factory)  
  
        ' Do not change code in this method.  
    End Sub  
    ```  
  
    ```csharp  
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest,   
        Microsoft.Office.Tools.Outlook.Factory factory)  
    {  
        // Do not change code in this method.  
    }  
    ```  
  
5.  プロジェクトに新しい Outlook フォーム領域アイテムを追加します。 新しいフォーム領域の分離コード ファイルを開き、ファイルの *YourNewFormRegion*`Factory` および `WindowFormRegionCollection` クラスを見つけて、これらのクラスをクリップボードにコピーします。  
  
6.  プロジェクトに追加した新しいフォーム領域を削除します。  
  
7.  再ターゲットのプロジェクトの作業を更新するフォーム領域の分離コード ファイルで、 *YourOriginalFormRegion*`Factory` および `WindowFormRegionCollection` クラスを見つけ、新しいフォーム領域からコピーしたコードに置き換えます。  
  
8.  *YourNewFormRegion*`Factory` と `WindowFormRegionCollection` クラスで、 *YourNewFormRegion* クラスしへのすべての参照を検索し、それぞれの参照先を、代わりに *YourOriginalFormRegion* クラスに変更します。 たとえば、更新するフォーム領域の名前が `SalesDataFormRegion` で、手順 5 で作成した新しいフォーム領域の名前が `FormRegion1`の場合、 `FormRegion1` のすべての参照を `SalesDataFormRegion`に変更します。  
  
#### <a name="to-update-the-generated-code-for-a-form-region-that-you-imported-from-outlook"></a>Outlook からインポートしたフォーム領域の生成されたコードを更新するには  
  
1.  コード エディターでフォーム領域の分離コード ファイルを開きます。 このファイル名は *YourFormRegion*.Designer.cs または *YourFormRegion*.Designer.vb です。 Visual Basic プロジェクトでこのファイルを確認するには、 **ソリューション エクスプローラー** の **[すべてのファイルの表示]**ボタンをクリックします。  
  
2.  派生するように、フォーム領域クラスの宣言を変更<xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase>Microsoft.Office.Tools.Outlook.ImportedFormRegion の代わりにします。  
  
3.  次のコード例に示すように、フォーム領域クラスのコンストラクターを変更します。  
  
     .NET Framework 3.5 を対象とするプロジェクトのフォーム領域クラスのコンストラクターを、次のコード例に示します。  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(formRegion)  
    End Sub  
    ```  
  
    ```csharp  
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(formRegion)  
    {  
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);  
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);  
    }  
    ```  
  
     [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]を対象とするプロジェクトのフォーム領域クラスのコンストラクターのシグネチャを、次のコード例に示します。  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(Globals.Factory, formRegion)  
    End Sub  
    ```  
  
    ```csharp  
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(Globals.Factory, formRegion)  
    {  
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);  
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);  
    }  
    ```  
  
4.  フォーム領域クラスのコントロールを初期化する `InitializeControls` メソッドのコードの各行について、次に示すようにコードを変更します。  
  
     .NET Framework 3.5 を対象とするプロジェクトのコントロールを初期化する方法を、次のコード例に示します。 このコードでは、GetFormRegionControl メソッドは、返されるコントロールの種類を指定する型パラメーターを持ちます。  
  
    ```vb  
    Me.olkTextBox1 = Me.GetFormRegionControl(Of Microsoft.Office.Interop.Outlook.OlkTextBox)("OlkTextBox1")  
    ```  
  
    ```csharp  
    this.olkTextBox1 = this.GetFormRegionControl<Microsoft.Office.Interop.Outlook.OlkTextBox>("OlkTextBox1");  
    ```  
  
     [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]を対象とするプロジェクトのコントロールを初期化する方法を、次のコード例に示します。 このコードの <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase.GetFormRegionControl%2A> メソッドには、型パラメーターがありません。 初期化するコントロールの型に戻り値をキャストする必要があります。  
  
    ```vb  
    Me.olkTextBox1 = CType(GetFormRegionControl("OlkTextBox1"), Microsoft.Office.Interop.Outlook.OlkTextBox)  
    ```  
  
    ```csharp  
    this.olkTextBox1 = (Microsoft.Office.Interop.Outlook.OlkTextBox)GetFormRegionControl("OlkTextBox1");  
    ```  
  
5.  プロジェクトに新しい Outlook フォーム領域アイテムを追加します。 新しいフォーム領域の分離コード ファイルを開き、ファイルの *YourNewFormRegion*`Factory` および `WindowFormRegionCollection` クラスを見つけて、これらのクラスをクリップボードにコピーします。  
  
6.  プロジェクトに追加した新しいフォーム領域を削除します。  
  
7.  再ターゲットのプロジェクトの作業を更新するフォーム領域の分離コード ファイルで、 *YourOriginalFormRegion*`Factory` および `WindowFormRegionCollection` クラスを見つけ、新しいフォーム領域からコピーしたコードに置き換えます。  
  
8.  *YourNewFormRegion*`Factory` と `WindowFormRegionCollection` クラスで、 *YourNewFormRegion* クラスしへのすべての参照を検索し、それぞれの参照先を、代わりに *YourOriginalFormRegion* クラスに変更します。 たとえば、更新するフォーム領域の名前が `SalesDataFormRegion` で、手順 5 で作成した新しいフォーム領域の名前が `FormRegion1`の場合、 `FormRegion1` のすべての参照を `SalesDataFormRegion`に変更します。  
  
## <a name="instantiating-form-region-classes"></a>フォーム領域クラスのインスタンス化  
 特定のフォーム領域クラスを動的にインスタンス化するすべてのコードを変更する必要があります。 プロジェクトでは、.NET Framework 3.5 を対象とする、直接 Microsoft.Office.Tools.Outlook.FormRegionManifest などのフォーム領域クラス インスタンス化できます。 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とするプロジェクトの場合、これらのクラスはインターフェイスであるため、直接インスタンス化できません。  
  
 プロジェクトのターゲット フレームワークを変更するかどうか、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]後で、インターフェイスをインスタンス化 Globals.Factory プロパティによって提供されるメソッドを使用して必要があります。 Globals.Factory プロパティの詳細については、次を参照してください。 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)です。  
  
 次の表に、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とするプロジェクトのフォーム領域の型と、型のインスタンス化に使用するメソッドをリストします。  
  
|型|使用するファクトリ メソッド|  
|----------|---------------------------|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionCustomAction>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionCustomAction%2A>|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionInitializingEventArgs%2A>|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionManifest%2A>|  
  
## <a name="see-also"></a>参照  
 [Migrating Office Solutions to the .NET Framework 4 or later](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Outlook フォーム領域の作成](../vsto/creating-outlook-form-regions.md)  
  