---
title: "デザイナーの初期化とメタデータの構成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c0865b62cc2683a8197b5eb6cbc0599d6c063534
ms.lasthandoff: 02/22/2017

---
# <a name="designer-initialization-and-metadata-configuration"></a>デザイナーの初期化とメタデータの構成
デザイナーまたはコンポーネント デザイナーに関連付けられているメタデータとフィルターの属性の操作は、アプリケーションが異なるを処理する、特定のデザイナーによって使用されるツールを定義するための機構を提供<xref:System.Type>Visual Studio IDE を構成して、デザイナーをサポートする方法と、デザイナーを使用すると、タイミング (データ構造体、クラス、またはグラフのエンティティ) などのオブジェクト (インスタンスを**ツールボックス**カテゴリまたはタブを使用).</xref:System.Type>  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]デザイナーのまたはデザイナーのコンポーネントの初期化の制御、および VSPackage でそのメタデータの操作を容易にするためにいくつかのメカニズムを提供します。  
  
## <a name="initializing-metadata-and-configuration-information"></a>メタデータと構成情報の初期化  
 要求時に読み込まれている、ため vspackages にある場合がありますがによって読み込まれていない、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]デザイナーのインスタンスを作成する前に環境です。 そのため、vspackages にあるは、処理の作成時にデザイナーまたはデザイナー コンポーネントを構成するための標準的な機構を使用できない、<xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated>イベント</xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated>。 VSPackage でのインスタンスを実装する代わりに、<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>インターフェイスし、デザイン画面の拡張機能と呼ばれるカスタマイズを提供できる自らを登録します</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>。  
  
### <a name="customizing-initialization"></a>初期化をカスタマイズします。  
 デザイナー、コンポーネント、またはデザイナーの画面をカスタマイズする手順を示します。  
  
1.  デザイナーのメタデータを変更して、特定の方法を効果的に変更する<xref:System.Type>アクセス、または変換します</xref:System.Type>。  
  
     これは通常行うには、<xref:System.Drawing.Design.UITypeEditor>または<xref:System.ComponentModel.TypeConverter>メカニズム</xref:System.ComponentModel.TypeConverter></xref:System.Drawing.Design.UITypeEditor>。  
  
     次に例を<xref:System.Windows.Forms>-に基づいて設計者が初期化され、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境を変更、<xref:System.Drawing.Design.UITypeEditor>の<xref:System.Web.UI.WebControls.Image>リソース マネージャーを使用して、ファイル システムではなく、ビットマップを取得する、デザイナーで使用されるオブジェクト</xref:System.Web.UI.WebControls.Image></xref:System.Drawing.Design.UITypeEditor></xref:System.Windows.Forms>。  
  
2.  イベントにサブスクライブするか、プロジェクトの構成情報を取得して、環境と統合します。 プロジェクトの構成情報を取得し、取得することでイベントをサブスクライブすることができます、<xref:System.ComponentModel.Design.ITypeResolutionService>インターフェイス</xref:System.ComponentModel.Design.ITypeResolutionService>。  
  
3.  適切なアクティブ化してユーザー環境の変更**ツールボックス**カテゴリのインスタンスを適用することで、デザイナーの適用性を制限することで、<xref:System.ComponentModel.ToolboxItemFilterAttribute>デザイナー クラス</xref:System.ComponentModel.ToolboxItemFilterAttribute>。  
  
### <a name="designer-initialization-by-a-vspackage"></a>VSPackage でデザイナーの初期化  
 VSPackage では、によってデザイナーの初期化を処理する必要があります。  
  
1.  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>クラス</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>を実装するオブジェクトを作成します。  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension><xref:Microsoft.VisualStudio.Shell.Package>クラス</xref:Microsoft.VisualStudio.Shell.Package>と同じオブジェクト上クラスで実装されることはありません</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
2.  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension><xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute><xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute><xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>クラスには、 <xref:Microsoft.VisualStudio.Shell.Package>。</xref:Microsoft.VisualStudio.Shell.Package> VSPackage の実装を提供すること</xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute></xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute></xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>のインスタンスを適用することで、VSPackage のデザイナーの拡張機能のサポートを提供するよう</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>に実装するクラスを登録します。  
  
 すべてのデザイナーまたはデザイナーのコンポーネントが作成されたときに、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境。  
  
1.  各登録済みのデザイン画面の拡張機能のプロバイダーにアクセスします。  
  
2.  インスタンス化し、デザイン画面の拡張機能プロバイダーの各<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>オブジェクト</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>のインスタンスを初期化します  
  
3.  デザイン画面の拡張機能プロバイダーの各を呼び出して<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>メソッドまたは<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A>メソッド (必要に応じて).</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>  
  
 実装する場合、 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>、VSPackage のメンバーとしてオブジェクトのことを理解することが重要:</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境はどのようなメタデータの制御を提供していない、またはその他の構成設定可能`DesignSurfaceExtension`プロバイダーの変更します。 2 つ以上の`DesignSurfaceExtension`プロバイダーが競合する形で明確なされる最終的な変更を同じデザイナー機能を変更します。 最後に変更が適用されたは不確定はありません。  
  
2.  実装を明示的に制限するには、<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>オブジェクトのインスタンスを適用することで、特定のデザイナーを<xref:System.ComponentModel.ToolboxItemFilterAttribute>その実装にします</xref:System.ComponentModel.ToolboxItemFilterAttribute></xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>。 詳細については**ツールボックス**項目のフィルター処理<xref:System.ComponentModel.ToolboxItemFilterAttribute>および<xref:System.ComponentModel.ToolboxItemFilterType>.</xref:System.ComponentModel.ToolboxItemFilterType></xref:System.ComponentModel.ToolboxItemFilterAttribute>を参照してください  
  
## <a name="additional-metadata-provisioning"></a>追加のメタデータのプロビジョニング  
 VSPackage には、デザイン時にデザイナーまたは以外のデザイナーのコンポーネントの構成を変更できます。  
  
 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>クラスをプログラムで使用するデザイナーを提供することを VSPackage に適用することもできます</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>。  
  
 インスタンス、<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>クラスを使用して、デザイン サーフェイス上で作成されたコンポーネントのメタデータを変更します</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>。 たとえば、いずれかで使用される既定のプロパティ ブラウザーを置き換えることができます<xref:System.Windows.Forms.CommonDialog>カスタム プロパティ ブラウザーでのオブジェクト</xref:System.Windows.Forms.CommonDialog>。  
  
 インスタンスで説明する変更<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>の VSPackage の実装に適用した<xref:Microsoft.VisualStudio.Shell.Package>2 つのスコープのいずれか:</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
-   指定したコンポーネントのすべての新しいインスタンスのグローバル--  
  
-   ローカル--現在 VSPackage によって提供されるデザイン サーフェイスで作成されたコンポーネントのインスタンスにのみ関連します。  
  
 `IsGlobal`のプロパティ、<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>の VSPackage の実装に適用したインスタンス<xref:Microsoft.VisualStudio.Shell.Package>このスコープを設定します</xref:Microsoft.VisualStudio.Shell.Package></xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>。  
  
 実装に属性を適用する<xref:Microsoft.VisualStudio.Shell.Package>で、<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A>のプロパティ、<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>オブジェクトに設定して`true`、全体のブラウザーが次のように、変更[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境:</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> </xref:Microsoft.VisualStudio.Shell.Package>  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
 グローバル フラグが設定した場合`false`メタデータの変更は現在の VSPackage でサポートされている現在のデザイナーにローカル。  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  現時点では、デザイン画面では、作成するコンポーネントのみがサポートし、したがってコンポーネントだけがローカルのメタデータを与えることをがします。 上記の例ではしようとしていたように、プロパティを変更する、`Color`オブジェクトのプロパティです。 場合`false`グローバル フラグには、渡された`CustomBrowser`ことはありませんが、デザイナーは、のインスタンスを実際に作成されるためが表示されます`Color`します。 グローバル フラグに設定`false`コントロール、タイマー、およびダイアログ ボックスなどのコンポーネント役に立ちます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension></xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute></xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType></xref:System.ComponentModel.ToolboxItemFilterType>   
 [デザイン時サポートを拡張します。](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
