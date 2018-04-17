---
title: パッケージとプロジェクト アイテムの展開情報を提供する |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SafeControlEntries
- VS.SharePointTools.Project.ProjectOutputReference
- VS.SharePointTools.Project.FeatureProperties
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature properties
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
- feature properties [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature receiver
- feature receiver [SharePoint development in Visual Studio]
- safe controls [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 078715380bb5ddc570d745d76fabe4d8a264eef0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="providing-packaging-and-deployment-information-in-project-items"></a>プロジェクト項目でのパッケージ化と配置の情報の提供
  すべての SharePoint プロジェクト項目[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]プロジェクトが SharePoint に配置されるときに、追加のデータを指定するのに使用できるプロパティがあります。 選択できるプロパティは次のとおりです。  
  
-   機能のプロパティ  
  
-   フィーチャー レシーバー  
  
-   プロジェクト出力参照  
  
-   安全なコントロール エントリ  
  
 これらのプロパティに表示されます、**プロパティ**ウィンドウです。  
  
## <a name="feature-properties"></a>機能のプロパティ  
 使用して、**フィーチャーのプロパティ**プロパティをこの機能を使用するデータを指定します。 機能のプロパティのデータは、SharePoint に展開するときに、機能に含まれている値 (キー/値のペアとして格納されます) のセットです。 フィーチャーが配置されると、そのプロパティ値にコードでアクセスできるようになります。  
  
 プロジェクト アイテムをフィーチャーのプロパティの値を追加すると、値は、アイテムのフィーチャーのマニフェスト内の要素として追加されます。 ビジネス データ接続 (BDC) モデル プロジェクトでは、たとえば、ModelFileName 機能のプロパティとして表示されます。  
  
```  
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />   
```  
  
 機能プロパティ値を設定した後は、プロジェクトの .spdata ファイルで FeatureProperty 要素として追加されます。 SharePoint でプロパティにアクセスする方法については、次を参照してください。 [SPFeaturePropertyCollection クラス](http://go.microsoft.com/fwlink/?LinkId=177391)です。  
  
 すべてのプロジェクト項目からプロパティ値を同一の機能は、フィーチャーのマニフェストで一緒にマージされます。 ただし、2 つの別のプロジェクト項目は、一致しない値を持つ同一の機能プロパティのキーを指定する場合、検証エラーが発生します。  
  
 機能ファイルに直接フィーチャーのプロパティを追加する (* .feature) を呼び出し、 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint オブジェクト モデルのメソッド<xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>です。 このメソッドを使用する場合、同じルール フィーチャーのプロパティで同一のフィーチャーのプロパティ値を追加する方法も適用されている機能ファイルに直接追加のプロパティに注意してください。  
  
## <a name="feature-receiver"></a>フィーチャー レシーバー  
 フィーチャー レシーバーは、プロジェクト項目に特定のイベントが発生するときに実行されるコードの対象フィーチャーでです。 たとえば、機能がインストールされている、アクティブ化、またはアップグレード時に実行されるフィーチャー レシーバーを定義できます。 説明に従って、機能に直接追加するフィーチャー レシーバーを追加する方法の 1 つ[チュートリアル: フィーチャー イベント レシーバーの追加](../sharepoint/walkthrough-add-feature-event-receivers.md)です。 別の方法は、フィーチャー レシーバーのクラス名とでアセンブリを参照する、**フィーチャー レシーバー**プロパティです。  
  
### <a name="direct-method"></a>直接的な方法  
 コード ファイルが下に置かれて、機能するフィーチャー レシーバーを直接追加する場合、**機能**ソリューション エクスプ ローラー内のノードです。 SharePoint ソリューションをビルドするときに、コードは、アセンブリにコンパイルされ、SharePoint に配置します。 既定では、フィーチャーのプロパティ**レシーバー アセンブリ**と**レシーバー クラス**クラス名とアセンブリを参照します。  
  
### <a name="reference-method"></a>Reference メソッド  
 フィーチャー レシーバーを追加する別の方法を使用して、**フィーチャー レシーバー**フィーチャー レシーバー アセンブリを参照するプロジェクト アイテムのプロパティです。 フィーチャー レシーバーのプロパティの値が 2 つのサブプロパティ:**アセンブリ**と**クラス名**です。 アセンブリが完全修飾を使用する必要があります、「強力な」名とクラス名が完全な型名にする必要があります。 詳細については、「[厳密な名前付きアセンブリ](http://go.microsoft.com/fwlink/?LinkID=169573)」を参照してください。 を SharePoint にソリューションを配置した後は、の機能は、フィーチャーのイベントを処理するのに参照先のフィーチャー レシーバーを使用します。  
  
 ソリューションのビルド時に機能とそのプロジェクトでフィーチャー レシーバーのプロパティ値は、SharePoint ソリューション (.wsp) ファイルのフィーチャー マニフェストの機能の要素の ReceiverAssembly と ReceiverClass 属性を設定するをマージします。 そのため、プロジェクト項目および機能のアセンブリとクラス名のプロパティ値がどちらも指定されている場合、プロジェクト項目およびフィーチャーのプロパティ値は一致しなければなりません。 値が一致しない場合、検証エラーが表示されます。 プロジェクト項目を使用する場合は、その機能を使用して、異なるフィーチャー レシーバー アセンブリを参照する、別の機能に移動します。  
  
 パッケージにアセンブリ ファイル自体を含める必要がありますもされていないサーバーにフィーチャー レシーバー アセンブリを参照する場合[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]するには追加できません。 システムのアセンブリ ファイルをコピー、機能を展開するときに[!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)]または SharePoint の物理ディレクトリにある Bin フォルダーです。 詳細については、次を参照してください。 方法:[する方法: 追加およびその他のアセンブリを削除する](../sharepoint/how-to-add-and-remove-additional-assemblies.md)です。  
  
 フィーチャー レシーバーの詳細については、次を参照してください。[フィーチャー イベント レシーバー](http://go.microsoft.com/fwlink/?LinkID=169574)と[機能イベント](http://go.microsoft.com/fwlink/?LinkID=169575)です。  
  
## <a name="project-output-references"></a>プロジェクト出力参照  
 プロジェクト出力参照プロパティには、プロジェクト項目の実行に必要なアセンブリなど、依存関係を指定します。 たとえば、ソリューションに、BDC プロジェクトとクラス プロジェクトとします。 BDC プロジェクトには、クラス プロジェクトによって出力されるアセンブリの依存関係が存在する場合は、BDC プロジェクトのプロジェクト出力参照プロパティ内のアセンブリを参照できます。 BDC プロジェクトがパッケージされるときは、パッケージの依存アセンブリが含まれています。  
  
 プロジェクト出力参照は、通常、アセンブリが、場合によっては (Silverlight プロジェクトの場合) などの他のファイルの種類を指定できます。  
  
 詳細については、次を参照してください。[する方法: プロジェクト出力参照を追加](../sharepoint/how-to-add-a-project-output-reference.md)です。  
  
## <a name="safe-control-entries"></a>安全なコントロール エントリ  
 SharePoint では、特定のコントロールに信頼されていないユーザーへのアクセスを制限するための安全なコントロール エントリのセキュリティ メカニズムを提供します。 仕様では、SharePoint できる信頼されていないアップロードし、SharePoint サーバー上の ASPX ページを作成します。 SharePoint へのアクセスが制限をこれらのユーザーが安全でないコードの ASPX ページを追加することを防ぐために*安全なコントロール*です。 安全なコントロール ASPX コントロールと Web パーツがセキュリティで保護されたとして指定され、サイト上のすべてのユーザーが使用できます。 詳細については、次を参照してください。[手順 4: セーフ コントロール リストに、Web パーツの追加](http://go.microsoft.com/fwlink/?LinkID=171014)です。  
  
 内のすべての SharePoint プロジェクト項目[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]というプロパティを持つ**安全なコントロール エントリ**を持つ 2 つのブール サブプロパティ:**セーフ**と**スクリプトに対して安全**です。 [安全] プロパティでは、信頼されていないユーザーがコントロールにアクセスできるかどうかを指定します。 スクリプトに対して安全プロパティは、信頼されていないユーザーが表示して、コントロールのプロパティを変更するかどうかを指定します。  
  
 安全なコントロール エントリは、アセンブリごとに参照されます。 プロジェクト アイテムの入力することによって、プロジェクトのアセンブリに安全なコントロール エントリを追加する**安全なコントロール エントリ**プロパティです。 ただし、追加することも安全なコントロール エントリを通じて、プロジェクトのアセンブリを**詳細** タブで、**パッケージ デザイナー**パッケージに追加のアセンブリを追加するとします。 詳細については、次を参照してください。[する方法: 安全なコントロールとしてマーク コントロール](../sharepoint/how-to-mark-controls-as-safe-controls.md)または[Web パーツ アセンブリを登録する安全なコントロールとして](http://go.microsoft.com/fwlink/?LinkID=171013)です。  
  
### <a name="xml-entries-for-safe-controls"></a>XML の安全なコントロール エントリ  
 プロジェクト項目またはプロジェクトのアセンブリに安全なコントロール エントリを追加するときの参照は、次の形式でパッケージ マニフェストに書き込まれます。  
  
```xml  
<Assemblies>  
    <Assembly Location="<assembly name>.dll"     
      DeploymentTarget="<'GlobalAssemblyCache' or 'WebApplication'">>  
        <SafeControls>  
            <SafeControl Assembly="<assembly name>.dll" Namespace=  
              "<SharePoint project name>" Safe="<true/false>"     
                TypeName="<control name>"   
                SafeAgainstScript="<true/false>" />  
        </SafeControls>  
    </Assembly>  
</Assemblies>  
```  
  
## <a name="see-also"></a>関連項目  
 [パッケージ化と SharePoint ソリューションの配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [モジュールを使用して、ソリューション内のファイルのインクルード](../sharepoint/using-modules-to-include-files-in-the-solution.md)   
 [SharePoint のパッケージ化と配置の拡張](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  