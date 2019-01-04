---
title: パッケージとプロジェクト項目で展開情報の提供 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SafeControlEntries
- VS.SharePointTools.Project.ProjectOutputReference
- VS.SharePointTools.Project.FeatureProperties
dev_langs:
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
ms.openlocfilehash: 5ec29871cc6e5062f2d44fb8938872b5f0531f2a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53843022"
---
# <a name="provide-packaging-and-deployment-information-in-project-items"></a>プロジェクト項目でパッケージ化と配置の情報を提供します。
  すべての SharePoint プロジェクト アイテム[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]プロジェクトが SharePoint に配置されるときに、追加のデータを提供するのに使用できるプロパティがあります。 選択できるプロパティは次のとおりです。  
  
- 機能のプロパティ  
  
- フィーチャー レシーバー  
  
- プロジェクト出力参照  
  
- 安全なコントロール エントリ  
  
  これらのプロパティに表示されます、**プロパティ**ウィンドウ。  
  
## <a name="feature-properties"></a>フィーチャーのプロパティ
 使用して、**機能プロパティ**機能を使用するデータを指定するプロパティ。 機能プロパティのデータは、SharePoint に展開する場合に、機能に含まれている一連の値 (キー/値ペアとして格納されます)。 フィーチャーが配置されると、そのプロパティ値にコードでアクセスできるようになります。  
  
 プロジェクト アイテムをフィーチャー プロパティの値を追加すると、値は、項目のフィーチャーのマニフェスト内の要素として追加されます。 ビジネス データ接続 (BDC) モデル プロジェクトでは、たとえば、ModelFileName フィーチャーのプロパティとして表示されます。  
  
```xml  
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />   
```  
  
 フィーチャー プロパティの値を設定した後、プロジェクトの FeatureProperty 要素として追加された *.spdata*ファイル。 Sharepoint プロパティへのアクセス方法の詳細については、次を参照してください。 [SPFeaturePropertyCollection クラス](http://go.microsoft.com/fwlink/?LinkId=177391)します。  
  
 すべてのプロジェクト項目からプロパティ値を同一の機能は、機能マニフェストで一緒にマージされます。 ただし、2 つの別のプロジェクト項目では、一致しない値を持つ同じの機能プロパティのキーを指定する場合は、検証エラーが発生します。  
  
 機能ファイルに直接機能のプロパティを追加する (*.feature*) を呼び出し、 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint オブジェクト モデルのメソッド<xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>します。 このメソッドを使用する場合は、同じルール機能のプロパティでプロパティの値を同一の機能を追加する方法については、機能ファイルに直接追加プロパティにも適用されます。  
  
## <a name="feature-receiver"></a>フィーチャー レシーバー
 フィーチャー レシーバーは、プロジェクト項目に特定のイベントが発生したときに実行されるコードには、機能が含まれているのです。 たとえば、機能がインストールされている、アクティブ化、またはアップグレード時に実行されるフィーチャー レシーバーを定義できます。 」の説明に従って、機能に直接追加するフィーチャー レシーバーを追加する方法の 1 つ[チュートリアル。フィーチャー イベント レシーバーの追加](../sharepoint/walkthrough-add-feature-event-receivers.md)します。 別の方法は、フィーチャー レシーバー クラス名とアセンブリを参照する、**フィーチャー レシーバー**プロパティ。  
  
### <a name="direct-method"></a>ダイレクト メソッド
 コード ファイルがの下に配置機能をフィーチャー レシーバーを直接追加すると、**機能**ソリューション エクスプ ローラーでノード。 SharePoint ソリューションをビルドするコードはアセンブリにコンパイルし、SharePoint に配置します。 既定では、フィーチャーのプロパティによって**レシーバー アセンブリ**と**レシーバー クラス**クラス名とアセンブリを参照します。  
  
### <a name="reference-method"></a>Reference メソッド
 フィーチャー レシーバーを追加する別の方法を使用して、**フィーチャー レシーバー**フィーチャー レシーバー アセンブリを参照するプロジェクト項目のプロパティ。 フィーチャー レシーバーのプロパティの値は、2 つのサブプロパティを含みます。**アセンブリ**と**クラス名**します。 アセンブリが完全修飾を使用する必要があります、「強力な」名とクラス名は完全な型名にする必要があります。 詳細については、「[厳密な名前付きアセンブリ](http://go.microsoft.com/fwlink/?LinkID=169573)」を参照してください。 を SharePoint にソリューションをデプロイした後、この機能は、機能のイベントを処理するために参照されるフィーチャー レシーバーを使用します。  
  
 ソリューションのビルド時、機能、機能の受信側プロパティの値とそのプロジェクトが SharePoint ソリューションのフィーチャー マニフェストに、Feature 要素の ReceiverAssembly と ReceiverClass 属性を設定するマージ (*.wsp*) ファイル。 したがって、プロジェクト項目と機能のアセンブリとクラス名のプロパティ値を両方指定する場合、プロジェクト項目とフィーチャー プロパティの値が一致する必要があります。 値が一致しない場合、検証エラーが表示されます。 プロジェクト項目を使用する場合は、その機能が使用するには、1 つ以外のフィーチャー レシーバー アセンブリを参照、別の機能に移動します。  
  
 パッケージにアセンブリ ファイル自体を含める必要がありますも既にサーバーではないにフィーチャー レシーバー アセンブリを参照する場合[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]するには追加できません。 システムのアセンブリ ファイルをコピー、機能を展開するときに[!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)]または SharePoint の物理ディレクトリの Bin フォルダー。 詳細については、次を参照してください。 方法。[方法: 追加およびその他のアセンブリを削除](../sharepoint/how-to-add-and-remove-additional-assemblies.md)します。  
  
 フィーチャー レシーバーの詳細については、次を参照してください。[フィーチャー イベント レシーバー](http://go.microsoft.com/fwlink/?LinkID=169574)と[機能イベント](http://go.microsoft.com/fwlink/?LinkID=169575)します。  
  
## <a name="project-output-references"></a>プロジェクト出力参照
 プロジェクト出力参照プロパティには、プロジェクト項目の実行に必要なアセンブリなどの依存関係を指定します。 たとえば、ソリューションに BDC プロジェクトとクラス プロジェクトとします。 BDC プロジェクトには、クラス プロジェクトの出力でのアセンブリに依存関係が存在する場合は、BDC プロジェクトのプロジェクト出力参照のプロパティでアセンブリを参照できます。 BDC プロジェクトをパッケージ化すると、パッケージの依存アセンブリが含まれます。  
  
 プロジェクト出力参照がアセンブリでは、通常が、場合によっては (Silverlight プロジェクトの場合) などの他のファイルの種類を指定できます。  
  
 詳細については、「[方法 :プロジェクト出力参照を追加](../sharepoint/how-to-add-a-project-output-reference.md)します。  
  
## <a name="safe-control-entries"></a>安全なコントロール エントリ
 SharePoint では、特定のコントロールに信頼されていないユーザーのアクセスを制限する、安全なコントロール エントリのセキュリティ メカニズムを提供します。 設計では、SharePoint は、信頼されていないユーザーをアップロードし、SharePoint サーバー上の ASPX ページの作成を許可します。 SharePoint へのアクセスの制限をこれらのユーザーが ASPX ページに安全でないコードを追加することを防ぐために*安全なコントロール*します。 安全なコントロールは、ASPX コントロールおよび Web パーツをセキュリティで保護されたとして指定して、サイト上のすべてのユーザーが使用できます。 詳細については、次を参照してください。[手順 4。安全なコントロールの一覧に、Web パーツを追加する](http://go.microsoft.com/fwlink/?LinkID=171014)します。  
  
 すべての SharePoint プロジェクト アイテムで[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]という名前のプロパティを持つ**安全なコントロール エントリ**を持つ 2 つのブール型のサブプロパティ。**安全な**と**スクリプトに対して安全**します。 安全なプロパティは、信頼されていないユーザーがコントロールにアクセスできるかどうかを指定します。 スクリプトに対して安全プロパティは、信頼されていないユーザーが表示し、コントロールのプロパティを変更するかどうかを指定します。  
  
 安全なコントロール エントリは、アセンブリに参照されます。 プロジェクト アイテムの入力することによって、プロジェクトのアセンブリに安全なコントロール エントリを追加する**安全なコントロール エントリ**プロパティ。 ただし、追加することも安全なコントロール エントリを使用して、プロジェクトのアセンブリ、**詳細** タブで、**パッケージ デザイナー**パッケージに追加のアセンブリを追加するとします。 詳細については、「[方法 :安全なコントロールとしてマークが制御](../sharepoint/how-to-mark-controls-as-safe-controls.md)または[安全なコントロールとして、Web パーツ アセンブリを登録する](http://go.microsoft.com/fwlink/?LinkID=171013)します。  
  
### <a name="xml-entries-for-safe-controls"></a>XML の安全なコントロール エントリ
 プロジェクトのアセンブリまたはプロジェクト項目に安全なコントロール エントリを追加すると、参照は、次の形式でパッケージ マニフェストに書き込まれます。  
  
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
 [パッケージと SharePoint ソリューションの配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [モジュールを使用して、ソリューションにファイルを含める](../sharepoint/using-modules-to-include-files-in-the-solution.md)   
 [SharePoint のパッケージ化と配置を拡張します。](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
