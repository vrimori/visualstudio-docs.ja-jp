---
title: "プロジェクト項目でのパッケージ化と配置の情報の提供"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.SafeControlEntries"
  - "VS.SharePointTools.Project.ProjectOutputReference"
  - "VS.SharePointTools.Project.FeatureProperties"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "フィーチャーのプロパティ [Visual Studio での SharePoint 開発]"
  - "フィーチャー レシーバー [Visual Studio での SharePoint 開発]"
  - "プロジェクト出力参照 [Visual Studio での SharePoint 開発]"
  - "安全なコントロール [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発, 高度なパッケージ化ツール"
  - "Visual Studio での SharePoint 開発, フィーチャーのプロパティ"
  - "Visual Studio での SharePoint 開発, フィーチャー レシーバー"
  - "Visual Studio での SharePoint 開発, プロジェクト出力参照"
  - "Visual Studio での SharePoint 開発, 安全なコントロール"
ms.assetid: 209ff3b9-d701-4d27-9d24-005fcc811cbe
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# プロジェクト項目でのパッケージ化と配置の情報の提供
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] のすべての SharePoint プロジェクト項目には、プロジェクトが SharePoint に配置されるときに追加のデータを提供するために使用できるプロパティがあります。  選択できるプロパティは次のとおりです。  
  
-   フィーチャーのプロパティ  
  
-   フィーチャー レシーバー  
  
-   プロジェクト出力参照  
  
-   安全なコントロール エントリ  
  
 これらのプロパティは **\[プロパティ\]** ウィンドウに表示されます。  
  
## フィーチャーのプロパティ  
 フィーチャーが使用するデータを指定するには、**\[フィーチャーのプロパティ\]** プロパティを使用します。  フィーチャーのプロパティのデータは、フィーチャーが SharePoint に配置されるときに一緒に含まれる一連の値 \(キー\/値のペアとして格納されます\) です。  フィーチャーが配置されると、そのプロパティ値にコードでアクセスできるようになります。  
  
 プロジェクト項目にフィーチャーのプロパティの値を追加すると、その値は、その項目のフィーチャー マニフェストに要素として追加されます。  以下は、Business Data Connectivity \(BDC\) モデル プロジェクトの ModelFileName というフィーチャーのプロパティの例です。  
  
```  
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />   
```  
  
 フィーチャーのプロパティの値を設定すると、その値は、プロジェクトの .spdata ファイルに FeatureProperty 要素として追加されます。  SharePoint のプロパティにアクセスする方法については、"参照してください [SPFeaturePropertyCollection クラス](http://go.microsoft.com/fwlink/?LinkId=177391)。  
  
 フィーチャー マニフェストでは、同じフィーチャーのプロパティの値がすべてのプロジェクト項目についてマージされますが、  2 つの異なるプロジェクト項目で指定されているフィーチャーのプロパティのキーが同じで値が違っていると、検証エラーが発生します。  
  
 フィーチャーのプロパティを直接フィーチャー ファイル \(\*.feature\) に追加するには、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint オブジェクト モデルの <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A> メソッドを呼び出します。  このメソッドを使用する場合は、同じフィーチャーのプロパティの値の追加について、\[フィーチャーのプロパティ\] を使用する場合と同じ規則が、直接フィーチャー ファイルに追加するプロパティにも適用されることに注意してください。  
  
## フィーチャー レシーバー  
 フィーチャー レシーバーとは、プロジェクト項目の対象フィーチャーで特定のイベントが発生した場合に実行されるコードです。  たとえば、フィーチャーがインストールされたときや、アクティブ化されたときや、アップグレードされたときに実行されるフィーチャー レシーバーを定義することができます。  フィーチャー レシーバーを追加するには、「[チュートリアル: フィーチャーのイベント レシーバーの追加](../sharepoint/walkthrough-add-feature-event-receivers.md)」の説明に従って直接フィーチャーに追加する方法と、  **\[フィーチャー レシーバー\]** プロパティでフィーチャー レシーバーのクラス名とアセンブリを参照する方法があります。  
  
### 直接追加する方法  
 フィーチャー レシーバーを直接フィーチャーに追加すると、ソリューション エクスプローラーの **\[フィーチャー\]** ノードにコード ファイルが配置されます。  SharePoint ソリューションをビルドすると、そのコードがアセンブリにコンパイルされて SharePoint に配置されます。  フィーチャーのプロパティの **\[レシーバー アセンブリ\]** と **\[レシーバー クラス\]** は既定でそのクラス名とアセンブリを参照します。  
  
### 参照する方法  
 フィーチャー レシーバーを追加するもう 1 つの方法では、プロジェクト項目の **\[フィーチャー レシーバー\]** プロパティを使用してフィーチャー レシーバー アセンブリを参照します。  \[フィーチャー レシーバー\] プロパティ値には、**\[アセンブリ\]** と **\[クラス名\]** という 2 つのサブプロパティがあります。  \[アセンブリ\] にはアセンブリの "厳密な" 完全修飾名を、\[クラス名\] にはクラスの完全な型名を指定する必要があります。  詳細については、参照します [Strong\-Named Assemblies](http://go.microsoft.com/fwlink/?LinkID=169573)。  ソリューションを SharePoint に配置すると、フィーチャーがその参照先のフィーチャー レシーバーを使用してフィーチャー イベントを処理するようになります。  
  
 ソリューションのビルド時に、フィーチャーとそのプロジェクトのフィーチャー レシーバー プロパティの値がマージされて、SharePoint ソリューション \(.wsp\) ファイルのフィーチャー マニフェストで Feature 要素の ReceiverAssembly 属性と ReceiverClass 属性が設定されます。  したがって、プロジェクト項目とフィーチャーの両方で \[アセンブリ\] プロパティと \[クラス名\] プロパティの値が指定されている場合は、プロジェクト項目とフィーチャーのプロパティの値が一致する必要があります。  値が一致しない場合は検証エラーが返されます。  フィーチャーで使用されているのとは別のフィーチャー レシーバー アセンブリをプロジェクト項目で参照するには、そのプロジェクト項目を別のフィーチャーに移動します。  
  
 まだサーバー上にないフィーチャー レシーバー アセンブリを参照する場合は、そのアセンブリ ファイルもパッケージに含める必要があります。[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] では追加されません。  フィーチャーを配置すると、そのアセンブリ ファイルがシステムの[!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] か SharePoint 物理ディレクトリの Bin フォルダーにコピーされます。  詳細については、「[方法: アセンブリを追加および削除する](../sharepoint/how-to-add-and-remove-additional-assemblies.md)」を参照してください。  
  
 フィーチャー レシーバーの詳細については、[フィー チャーのイベント レシーバー](http://go.microsoft.com/fwlink/?LinkID=169574) 参照します [フィー チャーのイベント](http://go.microsoft.com/fwlink/?LinkID=169575)。  
  
## プロジェクト出力参照  
 \[プロジェクト出力参照\] プロパティは、プロジェクト項目の実行に必要な依存関係 \(アセンブリなど\) を指定します。  たとえば、ソリューションに BDC プロジェクトとクラス プロジェクトがあり、  クラス プロジェクトの出力であるアセンブリに BDC プロジェクトが依存している場合は、そのアセンブリを BDC プロジェクトの \[プロジェクト出力参照\] プロパティで参照できます。  これにより、BDC プロジェクトがパッケージ化されるときにその依存アセンブリがパッケージに含まれるようになります。  
  
 プロジェクト出力参照はアセンブリであるのが一般的ですが、場合によっては \(Silverlight プロジェクトの場合など\)、その他の種類のファイルであることもあります。  
  
 詳細については、「[方法: プロジェクト出力参照を追加する](../sharepoint/how-to-add-a-project-output-reference.md)」を参照してください。  
  
## 安全なコントロール エントリ  
 SharePoint には、安全なコントロール エントリと呼ばれるセキュリティ機構があります。これにより、信頼されていないユーザーのアクセスを特定のコントロールで制限できます。  SharePoint では、信頼されていないユーザーも SharePoint サーバーに ASPX ページをアップロードしたり作成したりできるようになっていますが、  ASPX ページにアンセーフ コードが追加されるのを防ぐために、信頼されていないユーザーの*安全なコントロール*へのアクセスが制限されます。  安全なコントロールとは、安全として指定されている ASPX コントロールと Web パーツで、サイトのユーザーはだれでも使用できます。  詳細については、参照します [手順 4: 安全なコントロールのリストに Web パーツを追加します。](http://go.microsoft.com/fwlink/?LinkID=171014)。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] のすべての SharePoint プロジェクト項目に **\[安全なコントロール エントリ\]** という 2 ブール サブプロパティを含むプロパティがあります: **\[安全\]** と **\[スクリプトに対して安全\]**。  安全プロパティは、信頼されていないユーザーがコントロールにアクセスできるかどうかを指定します。  \[スクリプトに対して安全\] プロパティは、信頼されていないユーザーがコントロールのプロパティを表示したり変更したりできるかどうかを指定します。  
  
 安全なコントロール エントリはアセンブリに基づいて参照されます。  安全なコントロール エントリをプロジェクトのアセンブリに追加するには、それらをプロジェクト項目の **\[安全なコントロール エントリ\]** プロパティに入力します。  パッケージに追加のアセンブリを追加するときに、**パッケージ デザイナー**の **\[詳細設定\]** タブを使用して追加することもできます。  詳細については、[方法: コントロールを安全なコントロールとしてマークする](../sharepoint/how-to-mark-controls-as-safe-controls.md) を参照します [安全なコントロールとして Web Part Assembly の登録](http://go.microsoft.com/fwlink/?LinkID=171013)。  
  
### 安全なコントロールの XML エントリ  
 プロジェクト項目やプロジェクトのアセンブリに安全なコントロール エントリを追加すると、パッケージ マニフェストに次の形式で参照が書き込まれます。  
  
```  
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
  
## 参照  
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [モジュールを使用してソリューションにファイルを追加する](../sharepoint/using-modules-to-include-files-in-the-solution.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  