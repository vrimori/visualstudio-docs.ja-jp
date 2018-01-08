---
title: "デザイナーの初期化とメタデータの構成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 61624d9926f4d984386f1a8b3fe8a575ce465331
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="designer-initialization-and-metadata-configuration"></a>デザイナーの初期化とメタデータの構成
デザイナーまたはデザイナー コンポーネントに関連付けられているメタデータとフィルターの属性の操作は、さまざまな処理を特定のデザイナーで使用されるツールを定義するアプリケーションのメカニズムを備えています<xref:System.Type>オブジェクト (などのデータ構造体。クラス、またはグラフィカルなエンティティ) 場合は、デザイナーが利用可能なおよびデザイナーをサポートするために、Visual Studio IDE を構成する方法 (のインスタンスを**ツールボックス**カテゴリまたはタブを使用)。  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]をデザイナーのまたはデザイナーのコンポーネントの初期化の制御、および、VSPackage によってメタデータの操作を容易にするいくつかのメカニズムを提供します。  
  
## <a name="initializing-metadata-and-configuration-information"></a>メタデータと構成情報の初期化  
 要求時に読み込まれているため、Vspackage 可能性がありますいないによって読み込まれている、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]デザイナーのインスタンスを作成する前に環境。 したがって、Vspackage は、作成時に、これを処理するには、デザイナーまたはデザイナー コンポーネントを構成するための標準のメカニズムを使用できません、<xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated>イベント。 VSPackage がのインスタンスをどのように実装する代わりに、<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>インターフェイスし、デザイン画面の拡張機能と呼ばれる、カスタマイズを提供できる自身を登録します。  
  
### <a name="customizing-initialization"></a>初期化をカスタマイズします。  
 デザイナー、コンポーネント、またはデザイナーの画面をカスタマイズします。  
  
1.  デザイナーのメタデータを変更して、効果的に特定する方法を変更する<xref:System.Type>アクセス、または変換します。  
  
     通常これには、<xref:System.Drawing.Design.UITypeEditor>または<xref:System.ComponentModel.TypeConverter>メカニズムです。  
  
     たとえば、 <xref:System.Windows.Forms>-ベースのデザイナーは初期化され、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境を変更、<xref:System.Drawing.Design.UITypeEditor>の<xref:System.Web.UI.WebControls.Image>リソース マネージャーを使用して、ファイル システムではなくビットマップを取得するには、デザイナーで使用するオブジェクト。  
  
2.  イベントにサブスクライブするか、プロジェクトの構成情報を取得して、環境と統合します。 プロジェクトの構成情報を取得し、取得することによってイベントにサブスクライブできます、<xref:System.ComponentModel.Design.ITypeResolutionService>インターフェイスです。  
  
3.  適切なライセンス認証すれば、ユーザーの環境の変更**ツールボックス**カテゴリのインスタンスを適用することによって、デザイナーの適用性を制限することで、<xref:System.ComponentModel.ToolboxItemFilterAttribute>デザイナー クラス。  
  
### <a name="designer-initialization-by-a-vspackage"></a>VSPackage でデザイナーの初期化  
 VSPackage では、によってデザイナーの初期化を処理する必要があります。  
  
1.  実装するオブジェクトを作成する、<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>クラスです。  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>と同じオブジェクトのクラスを実装することはありません、<xref:Microsoft.VisualStudio.Shell.Package>クラスです。  
  
2.  実装するクラスを登録<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>のインスタンスを適用することで、VSPackage のデザイナーの拡張機能をサポートすることとして<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>、<xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>と<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>の VSPackage の実装を提供するクラスを<xref:Microsoft.VisualStudio.Shell.Package>.  
  
 特定のデザイナーやデザイナー コンポーネントが作成されたときに、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境。  
  
1.  登録済みのデザイン画面の拡張機能の各プロバイダーにアクセスします。  
  
2.  インスタンス化し、各デザイン画面の拡張機能プロバイダーのインスタンスを初期化<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>オブジェクト  
  
3.  デザイン画面の拡張機能プロバイダーの各を呼び出して<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>メソッドまたは<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A>メソッド (必要に応じて)。  
  
 実装する場合、 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> VSPackage のメンバーとしてオブジェクトのことを理解することが重要。  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境がメタデータに制御を提供していないまたはその他の構成の設定を特定`DesignSurfaceExtension`プロバイダーの変更します。 2 つ以上のことが`DesignSurfaceExtension`プロバイダーが、競合している方法で明確なされる最終的な変更を同じデザイナー機能を変更します。 不確定変更が最後に適用します。  
  
2.  実装を明示的に制限することは、<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>オブジェクトのインスタンスを適用することで、特定のデザイナーを<xref:System.ComponentModel.ToolboxItemFilterAttribute>その実装にします。 詳細については**ツールボックス**項目のフィルター処理しを参照してください、<xref:System.ComponentModel.ToolboxItemFilterAttribute>と<xref:System.ComponentModel.ToolboxItemFilterType>です。  
  
## <a name="additional-metadata-provisioning"></a>追加のメタデータのプロビジョニング  
 VSPackage では、デザイン時にデザイナーまたは以外のデザイナーのコンポーネントの構成を変更できます。  
  
 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>クラスをプログラムでは、使用できるデザイナーを提供する VSPackage に適用することもできます。  
  
 インスタンス、<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>クラスは、デザイン画面で作成されたコンポーネントのメタデータの変更に使用します。 たとえば、いずれかで使用される既定のプロパティ ブラウザーを置き換えることができます<xref:System.Windows.Forms.CommonDialog>カスタム プロパティ ブラウザーでのオブジェクト。  
  
 インスタンスによって提供される変更<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>の VSPackage の実装に適用される<xref:Microsoft.VisualStudio.Shell.Package>2 つのスコープのいずれかを持つことができます。  
  
-   指定したコンポーネントのすべての新しいインスタンスのグローバル--  
  
-   ローカル--、現在の VSPackage によって提供されるデザイン画面で作成されたコンポーネントのインスタンスにのみ関連します。  
  
 `IsGlobal`のプロパティ、<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>の VSPackage の実装に適用されるインスタンス<xref:Microsoft.VisualStudio.Shell.Package>がこのスコープを決定します。  
  
 実装に属性を適用する<xref:Microsoft.VisualStudio.Shell.Package>で、<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A>のプロパティ、<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>オブジェクトに設定して`true`、全体のブラウザーが次のように、変更[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境。  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
 グローバル フラグに設定された場合`false`メタデータの変更は、現在の VSPackage でサポートされている現在のデザイナーにローカル。  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  現時点では、デザイン画面では、作成するコンポーネントは、のみがサポート、したがってコンポーネントのみがローカルのメタデータを持つことができます。 上記の例ではしようとしていたように、プロパティを変更する、`Color`オブジェクトのプロパティです。 場合`false`グローバル フラグには、渡された`CustomBrowser`デザイナーが実際にはのインスタンスを作成するためには表示されない`Color`です。 グローバル フラグに設定`false`コントロール、タイマー、およびダイアログ ボックスなどのコンポーネントの役に立ちます。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [デザイン時サポートの拡張](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)