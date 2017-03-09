---
title: "チュートリアル: ツールボックス アイテムの構成の動的なカスタマイズ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ツールボックス [Visual Studio SDK]、コントロールの追加 (カスタム形式)"
ms.assetid: 761f44b7-c748-4ff5-921f-fc4f71784b0e
caps.latest.revision: 45
caps.handback.revision: 45
manager: "douge"
---
# チュートリアル: ツールボックス アイテムの構成の動的なカスタマイズ
このチュートリアルでは、マネージ VSPackage で <xref:System.Drawing.Design.ToolboxItem> オブジェクトの動的構成サポートを提供する方法について説明します。  
  
> [!NOTE]
>  カスタム コントロールをツールボックスに追加する最も簡単な方法は、Visual Studio SDK に含まれているツールボックス コントロール テンプレートを使用することです。 このトピックは、高度なツールボックス開発に関連しています。  
>   
>  テンプレートを使用してツールボックス コントロールを作成する方法の詳細については、「[方法: Windows フォームを使用するツールボックス コントロールを作成する](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md)」と「[WPF ツールボックス コントロールを作成します。](../extensibility/creating-a-wpf-toolbox-control.md)」を参照してください。  
  
 このチュートリアルでは、次の手順を実行します。  
  
1.  <xref:System.ComponentModel.ToolboxItemAttribute> クラスと <xref:System.Drawing.ToolboxBitmapAttribute> クラスを使用して、すべての**ツールボックス** コントロールを VSPackage オブジェクトに追加し、正しく登録します。  
  
2.  次の 2 つのコントロールを作成し、それぞれのアイコンを**ツールボックス**に追加します。  
  
    -   1 つのコントロールでは、関連付けられた既定の <xref:System.Drawing.Design.ToolboxItem> を宣言します。  
  
    -   もう 1 つのコントロールでは、<xref:System.Drawing.Design.ToolboxItem> クラスから派生した、関連付けられたカスタムの**ツールボックス** アイテムを宣言します。  
  
3.  <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> の実装を記述し、次の処理を実行してこれを登録します。  
  
    1.  フィルター クラスを定義します。このクラスは、<xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> クラスから派生し、この実装が動作する <xref:System.Drawing.Design.ToolboxItem> インスタンスを指定します。  
  
    2.  VSPackage の <xref:Microsoft.VisualStudio.Shell.Package> クラスを実装するクラスに、フィルター クラスを参照する <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute> を適用します。  
  
4.  VSPackage の <xref:Microsoft.VisualStudio.Shell.Package> クラスを実装するクラスに <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> を適用して、<xref:System.Drawing.Design.ToolboxItem> オブジェクトのプロバイダーとして VSPackage を登録します。  
  
5.  パッケージの読み込み時に、リフレクションを使用して、VSPackage が提供するすべての <xref:System.Drawing.Design.ToolboxItem> オブジェクトの一覧を生成します。  
  
6.  <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> イベントと <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> イベントのハンドラーを作成します。 これを行うと、VSPackage の <xref:System.Drawing.Design.ToolboxItem> オブジェクトが正常に読み込まれることが保証されます。  
  
7.  VSPackage にコマンドを実装して、**ツールボックス**の再初期化を強制します。  
  
## 必須コンポーネント  
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、「[Visual Studio SDK](../extensibility/visual-studio-sdk.md)」を参照してください。  
  
## Visual Studio パッケージのプロジェクト テンプレートの場所  
 Visual Studio パッケージのプロジェクト テンプレートは、**\[新しいプロジェクト\]** ダイアログの次の 3 つの場所にあります。  
  
1.  Visual Basic の機能拡張の下。 プロジェクトの既定の言語は Visual Basic です。  
  
2.  C\# の機能拡張の下。 プロジェクトの既定の言語は C\# です。  
  
3.  その他のプロジェクトの種類の機能拡張の下。 プロジェクトの既定の言語は C\+\+ です。  
  
## マネージ VSPackage の作成  
 マネージ VSPackage を作成するには、次の手順を実行します。  
  
#### ツールボックス アイテムを提供するマネージ VSPackage を作成するには  
  
1.  `ItemConfiguration` という名前の VSPackage を作成します。 詳細については、「[チュートリアル: Visual Studio パッケージ テンプレートを使用してメニュー コマンドを作成する](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md)」を参照してください。  
  
2.  **Visual Studio パッケージ** テンプレートに、メニュー コマンドを追加します。  
  
     Visual basic の場合は `Initialize ItemConfigurationVB`、Visual C\# の場合は `Initialize ItemConfigurationCS` という名前をコマンドに付けます。  
  
3.  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] の場合、生成されたプロジェクトのインポートされた名前空間の一覧に、次の名前空間を追加します。  
  
    -   Company.ItemConfiguration  
  
    -   System  
  
    -   System.ComponentModel  
  
    -   System.Drawing  
  
    -   System.Windows.Forms  
  
4.  <xref:System.Drawing.Design?displayProperty=fullName> .NET Framework コンポーネントに参照を追加します。  
  
 複数の言語に対してこのチュートリアルを行う場合は、生成されたアセンブリを明確に区別するためにプロジェクトを更新する必要があります。  
  
#### Visual Basic と Visual C\# の VSPackage を明確に区別するには  
  
1.  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] の場合:  
  
    1.  プロジェクトのプロパティを開いて、**\[アプリケーション\]** タブを選択します。  
  
         アセンブリ名を `ItemConfigurationVB` に変更し、既定の名前空間を `Company.ItemConfigurationVB` に変更します。  
  
    2.  **\[参照\]** タブをクリックします。  
  
         インポートされた名前空間の一覧を更新します。  
  
         Company.ItemConfiguration を削除します。  
  
         Company.ItemConfigurationVB を追加します。  
  
2.  [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] の場合:  
  
    1.  プロジェクトのプロパティを開いて、**\[アプリケーション\]** タブを選択します。  
  
         アセンブリ名を `ItemConfigurationCS` に変更し、既定の名前空間を `Company.ItemConfigurationCS` に変更します。  
  
    2.  コード エディターで ItemConfigurationPackage クラスを開きます。  
  
         リファクタリング ツールを使用して既存の名前空間の名前を変更するには、既存の名前空間の名前 `ItemConfiguration` を右クリックし、**\[リファクター\]** をポイントして、**\[名前の変更\]** をクリックします。 名前を `ItemConfigurationCS` に変更します。  
  
3.  すべての変更を保存します。  
  
#### 生成されたコードをテストするには  
  
1.  Visual Studio の実験用ハイブで VSPackage をコンパイルして起動します。  
  
2.  **\[ツール\]** メニューで、**\[Initialize Item Configuration VB\]** または **\[Initialize Item Configuration CS\]** をクリックします。  
  
     これでメッセージ ボックスが開き、パッケージのメニュー項目のハンドラーが呼び出されたことが示されます。  
  
3.  [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] の実験用バージョンを閉じます。  
  
## ツールボックス コントロールの作成  
 このセクションでは、関連付けられた既定の**ツールボックス** アイテムを宣言するユーザー コントロール `Control1` を作成し、登録します。 また、2 つ目のユーザー コントロール `Control2` と、<xref:System.Drawing.Design.ToolboxItem> クラスから派生した、関連付けられたカスタムの**ツールボックス** アイテム `Control2_ToolboxItem` を作成し、登録します。 Windows フォーム コントロールと <xref:System.Drawing.Design.ToolboxItem> クラスを作成する方法の詳細については、「[デザイン時の Windows フォーム コントロールの開発](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md)」を参照してください。  
  
#### 既定およびカスタムのツールボックス アイテムを作成するには  
  
1.  [チュートリアル: ツールボックス アイテムの自動読み込み](../Topic/Walkthrough:%20Autoloading%20Toolbox%20Items.md) の指示に従って、次のように、既定の**ツールボックス** アイテムおよびカスタムの**ツールボックス** アイテムを作成します。  
  
    1.  「既定値 ToolboxItem で使用する**ツールボックス** コントロールを作成するには」の手順を完了します。 このプロジェクトを参照するように <xref:System.ComponentModel.DescriptionAttribute> を更新します。  
  
         結果として得られる `Control1` クラスのコードは、次のようになります。  
  
         [!code-cs[DynamicToolboxMembers#01](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_1.cs)]
         [!code-vb[DynamicToolboxMembers#01](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_1.vb)]  
  
    2.  「ToolboxItem から派生したカスタム クラスを使用する**ツールボックス** コントロールを作成するには」の手順を完了します。 このプロジェクトを参照するように <xref:System.ComponentModel.DescriptionAttribute> を更新します。  
  
         結果として得られる `Control2` および `Control2_ToolboxItem` クラスのコードは、次のようになります。  
  
         [!code-vb[DynamicToolboxMembers#02](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_2.vb)]
         [!code-cs[DynamicToolboxMembers#02](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_2.cs)]  
  
2.  ファイルを保存します。  
  
## ビットマップ アイコンの埋め込み  
 各コントロールに適用される <xref:System.Drawing.ToolboxBitmapAttribute> 属性は、そのコントロールに関連付けるアイコンを指定します。 両方のコントロール用にビットマップを作成し、次のように名前を付けます。  
  
-   `Control1` クラスの場合、`Control1.bmp`。  
  
-   `Control2` クラスの場合、`Control2.bmp`。  
  
#### ツールボックス アイテムのビットマップ アイコンを埋め込むには  
  
1.  次のように、プロジェクトに新しいビットマップを追加します。  
  
    1.  **ソリューション エクスプローラー**で、VSPackage プロジェクトを右クリックし、**\[追加\]** をポイントして、**\[新しい項目\]** をクリックします。  
  
    2.  **\[新しい項目の追加\]** ダイアログ ボックスで **\[ビットマップ ファイル\]** を選択し、ビットマップの名前を入力します。  
  
2.  ビットマップ エディターを使用して、次のように 16x16 のアイコンを作成します。  
  
    1.  **\[表示\]** メニューの **\[プロパティ ウィンドウ\]** をクリックします。  
  
    2.  **\[プロパティ\]** ウィンドウで、**\[高さ\]** と **\[幅\]** を 16 に設定します。  
  
    3.  エディターを使用して、アイコン イメージを作成します。  
  
3.  **ソリューション エクスプローラー**で、ビットマップ項目を右クリックし、**\[プロパティ\]** をクリックします。  
  
4.  **\[ビルド アクション\]** プロパティを **\[埋め込みリソース\]** に設定します。  
  
5.  開いているすべてのファイルを保存します。  
  
## 動的なツールボックス構成プロバイダーの追加  
 このセクションでは、<xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> インターフェイスを実装するクラスを作成し、登録します。 このクラスは、**ツールボックス** コントロールを構成するために、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 統合開発環境 \(IDE\) によってインスタンス化され、使用されます。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> の実装のインスタンスは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 環境によってインスタンス化されるため、VSPackage の <xref:Microsoft.VisualStudio.Shell.Package> を実装するクラスに <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> インターフェイスを実装しないでください。  
  
#### ツールボックス コントロールの構成オブジェクトを作成し、登録するには  
  
1.  **ソリューション エクスプローラー**で、ItemConfiguration プロジェクトにクラスを追加し、`ToolboxConfig` という名前を付けます。  
  
2.  次の名前空間ステートメントをファイルに追加します。  
  
     [!code-cs[DynamicToolboxMembers#03](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_3.cs)]
     [!code-vb[DynamicToolboxMembers#03](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_3.vb)]  
  
3.  `ToolboxConfig` クラスが `public` で、<xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> インターフェイスを実装していることを確認します。  
  
4.  `ToolboxConfig` クラスに <xref:System.Runtime.InteropServices.GuidAttribute> と <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute> を適用します`.`  
  
    -   [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] の場合、`"ItemConfigurationVB, Version=*, Culture=*, PublicKeyToken=*"` のアセンブリ名を使用します。  
  
    -   [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] の場合、`"ItemConfigurationCS, Version=*, Culture=*, PublicKeyToken=*"` のアセンブリ名を使用します。  
  
     これで、現在の VSPackage を含むアセンブリによって提供される <xref:System.Drawing.Design.ToolboxItem> オブジェクトで動作するように `ToolboxConfig` クラスが制限されます。  
  
     [!code-cs[DynamicToolboxMembers#04](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_4.cs)]
     [!code-vb[DynamicToolboxMembers#04](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_4.vb)]  
  
     **\[ツール\]** メニューで **\[GUID の作成\]** をクリックして、GUID を生成することができます。**書式を角かっこ付きで**選択し、**\[コピー\]** をクリックして、コードに GUID を貼り付けます。 キーワード `GUID` を `Guid` に変更します。  
  
5.  メソッドが `Control1` と `Control2` の 2 つの <xref:System.Drawing.Design.ToolboxItem> クラスに対してのみ機能するように、<xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> インターフェイスの <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> メソッドを実装します。  
  
     <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> の実装は、次のようになるように、<xref:System.ComponentModel.ToolboxItemFilterAttribute> のインスタンスを 2 つの <xref:System.Drawing.Design.ToolboxItem> オブジェクトに適用します。  
  
    -   `Control1` によって実装される <xref:System.Drawing.Design.ToolboxItem> は、<xref:System.Windows.Forms.UserControl> オブジェクトを処理するデザイナーの**ツールボックス**でのみ使用できます。  
  
    -   `Control2` によって実装される <xref:System.Drawing.Design.ToolboxItem> は、<xref:System.Windows.Forms.UserControl> オブジェクトを処理するデザイナーの**ツールボックス**では使用できません。  
  
     [!code-cs[DynamicToolboxMembers#05](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_5.cs)]
     [!code-vb[DynamicToolboxMembers#05](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_5.vb)]  
  
## VSPackage 実装の変更  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] パッケージ テンプレートによって提供される VSPackage の既定の実装は、次の処理を実行するように変更する必要があります。  
  
-   **ツールボックス** アイテム プロバイダーとして登録します。  
  
-   動的な**ツールボックス** コントロール構成を VSPackage に提供するクラスを登録します。  
  
-   <xref:System.Drawing.Design.ToolboxService> を使用して、VSPackage アセンブリで提供されるすべての <xref:System.Drawing.Design.ToolboxItem> オブジェクトを読み込みます。  
  
-   <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> および <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> イベントを処理します。  
  
#### VSPackage でツールボックス アイテム プロバイダーのパッケージの実装を変更するには  
  
1.  コード エディターで ItemConfigurationPackage クラスを開きます。  
  
2.  ソリューション内の <xref:Microsoft.VisualStudio.Shell.Package> クラスの実装である `ItemConfigurationPackage` クラスの宣言を変更します。  
  
    1.  次の名前空間ステートメントをファイルに追加します。  
  
         [!code-vb[DynamicToolboxMembers#06](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_6.vb)]
         [!code-cs[DynamicToolboxMembers#06](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_6.cs)]  
  
    2.  **ツールボックス** アイテムのプロバイダーとして VSPackage を登録するには、パッケージに <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> を適用します。**ツールボックス** コントロールの動的構成のプロバイダーとして `ToolboxConfig` クラスを登録するには、パッケージに <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute> を適用します。  
  
         [!code-vb[DynamicToolboxMembers#07](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_7.vb)]
         [!code-cs[DynamicToolboxMembers#07](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_7.cs)]  
  
        > [!NOTE]
        >  <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> の唯一の引数は、VSPackage によって提供される <xref:System.Drawing.Design.ToolboxItem> のバージョンです。 この値を変更して、以前にキャッシュされた <xref:System.Drawing.Design.ToolboxItem> のバージョンが存在する場合でも、VSPackage を読み込むよう IDE に強制します。  
  
    3.  次のように、`ItemConfiguration` クラスに新しい 2 つの `private` フィールドを作成します。  
  
         `ToolboxItemList` という名前の <xref:System.Collections.ArrayList> メンバー。`ItemConfiguration` クラスが管理する <xref:System.Drawing.Design.ToolboxItem> オブジェクトの一覧を保持します。  
  
         `CategoryTab` という名前の <xref:System.String>。これに格納される**ツールボックス** タブは、`ItemConfiguration` クラスが管理する <xref:System.Drawing.Design.ToolboxItem> オブジェクトを保持するために使用されます。  
  
         [!code-vb[DynamicToolboxMembers#08](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_8.vb)]
         [!code-cs[DynamicToolboxMembers#08](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_8.cs)]  
  
     この変更の結果は、次のようになります。  
  
     [!code-vb[DynamicToolboxMembers#09](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_9.vb)]
     [!code-cs[DynamicToolboxMembers#09](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_9.cs)]  
  
3.  <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> および <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> イベントを処理するように、`OnRefreshToolbox` メソッドを定義します。  
  
     `OnRefreshToolbox` メソッドは、`ToolboxItemList` フィールドに格納されている <xref:System.Drawing.Design.ToolboxItem> オブジェクトの一覧を使用して、次の処理を実行します。  
  
    -   すべての <xref:System.Drawing.Design.ToolboxItem> オブジェクトを `CategoryTab` フィールドで定義されている**ツールボックス** タブから削除します。  
  
    -   `ToolboxItemList` フィールドに一覧されているすべての <xref:System.Drawing.Design.ToolboxItem> オブジェクトの新しいインスタンスを、**ツールボックス** タブに追加します。  
  
    -   **ツールボックス** タブをアクティブなタブとして設定します。  
  
     [!code-vb[DynamicToolboxMembers#10](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_10.vb)]
     [!code-cs[DynamicToolboxMembers#10](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_10.cs)]  
  
4.  [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] の場合、コンストラクターで `OnRefreshToolbox` メソッドを <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> および <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> イベントのイベント ハンドラーとして登録します。  
  
     [!code-cs[DynamicToolboxMembers#11](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_11.cs)]  
  
5.  <xref:System.Drawing.Design.ToolboxService?displayProperty=fullName> クラスの <xref:System.Drawing.Design.ToolboxService.GetToolboxItems%2A> メソッドを呼び出して `ToolboxItemList` フィールドに入力するように、`ItemConfigurationPackage` の `Initialize` メソッドを変更します。**ツールボックス** サービスは、現在実行中のアセンブリに定義されているすべての**ツールボックス** アイテム クラスを取得します。`ToolboxItemList` フィールドは、**ツールボックス** イベント ハンドラーによって、**ツールボックス** アイテムを読み込むために使用されます。  
  
     `Initialize` メソッドの末尾に、次のコードを追加します。  
  
     [!code-vb[DynamicToolboxMembers#12](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_12.vb)]
     [!code-cs[DynamicToolboxMembers#12](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_12.cs)]  
  
    > [!NOTE]
    >  演習として、VSPackage またはアイテムのバージョンをテストするためのメカニズムを開発し、VSPackage のバージョンが変更された場合または <xref:System.Drawing.Design.ToolboxItem> のバージョンが変更された場合のみ更新することができます。  
  
## ツールボックスの初期化  
  
#### ツールボックスを初期化するためのコマンドを実装するには  
  
-   `ItemConfigurationPackage` クラスで、メニュー項目のコマンド ハンドラーである `MenuItemCallBack` メソッドを変更します。  
  
     次のコードを使用して、`MenuItemCallBack` メソッドの既存の実装を置き換えます。  
  
     [!code-vb[DynamicToolboxMembers#13](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_13.vb)]
     [!code-cs[DynamicToolboxMembers#13](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_13.cs)]  
  
## ソリューションのビルドと実行  
 このチュートリアルの製品を実行するには、実験用ハイブで実行されている Visual Studio のインスタンスを使用します。  
  
#### このチュートリアルを実行するには  
  
1.  Visual Studio で、**\[ビルド\]** メニューの **\[ソリューションのリビルド\]** をクリックします。  
  
2.  実験用のレジストリ ハイブで F5 キーを押して、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の 2 番目のインスタンスを開始します。  
  
     実験用ハイブの使用方法の詳細については、「[実験用インスタンス](../extensibility/the-experimental-instance.md)」を参照してください。  
  
3.  **\[ツール\]** メニューをクリックします。  
  
     **\[Initialize ItemConfiguration VB\]** または **\[Initialize ItemConfiguration CS\]** という名前のコマンドが、数字 1 を含むアイコンとともにメニューの上部に表示されます。  
  
4.  新しい [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] または [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] の Windows フォーム アプリケーションを作成します。  
  
     <xref:System.Windows.Forms.Form>ベースのデザイナーが表示されます。  
  
5.  プロジェクトにユーザー コントロールを追加します。  
  
     ユーザー コントロール デザイナーが表示されます。  
  
6.  **ツールボックス**を固定して開いたままにし、2 つのデザイン ビューを切り替えます。  
  
     どの**ツールボックス** アイテムが表示され、どのアイテムが表示されないかは、どちらのデザイナーにフォーカスがあるかで決まることに注意してください。  
  
7.  1 つ目の**ツールボックス** アイテムをユーザー コントロールにドラッグし、`Control1` のインスタンスをユーザー コントロールに追加します。  
  
8.  2 つ目の**ツールボックス** アイテムをフォームにドラッグし、`Control2` のインスタンスをフォームに追加します。  
  
9. Windows アプリケーションをビルドします。  
  
     アプリケーションのユーザー コントロールが**ツールボックス**で使用できるようになっています。  
  
10. アプリケーションのユーザー コントロールをフォームに追加した後、アプリケーションをリビルドして実行します。  
  
     アプリケーションが実行したら、フォーム上の各コントロールをクリックして、関連するメッセージ ボックスを表示します。  
  
## 実装の分析  
 `assemblyFilter` パラメーターが <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute> クラス コンストラクターに存在するため、このチュートリアルで生成されたアセンブリ内の <xref:System.Drawing.Design.ToolboxItem> オブジェクトのみが `ToolboxConfg` クラスの <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> メソッドによって処理されます。  
  
 そのため、**ItemConfiguration Walkthrough** カテゴリが**ツールボックス**でアクティブになっている場合は必ず、`ToolboxConfg` クラスの <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> メソッドが呼び出され、<xref:System.ComponentModel.ToolboxItemFilterAttribute> インスタンスが `Control1` と `Control2` によって実装された <xref:System.Drawing.Design.ToolboxItem> オブジェクトに適用されます。  
  
## 参照  
 [ツールボックスの拡張](../misc/extending-the-toolbox.md)   
 [ツールボックスのサポート機能の登録](../misc/registering-toolbox-support-features.md)   
 [高度なツールボックス コントロールの開発](/visual-cpp/misc/advanced-toolbox-control-development)   
 [ツールボックスのチュートリアル](../misc/toolbox-walkthroughs.md)