---
title: デザイナーの初期化とメタデータの構成 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 58f103ae1dcf445c5bdfe322eeea7a88a7b25683
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843276"
---
# <a name="designer-initialization-and-metadata-configuration"></a>デザイナーの初期化とメタデータの構成
デザイナーまたはデザイナー コンポーネントに関連付けられているメタデータとフィルターの属性の操作は、アプリケーションで異なる処理するために、特定のデザイナーによって使用されるツールを定義するメカニズムを提供します<xref:System.Type>オブジェクト (などのデータ構造体。クラス、またはグラフィカル エンティティ)、デザイナーが使用可能な場合と、デザイナーをサポートするために、Visual Studio IDE を構成する方法 (インスタンスが**ツールボックス**カテゴリまたはタブを使用できる)。  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]デザイナーまたはデザイナーのコンポーネントの初期化のコントロールと、VSPackage によって、メタデータの操作を容易にいくつかのメカニズムを提供します。  
  
## <a name="initialize-metadata-and-configuration-information"></a>メタデータと構成情報を初期化します。  
 オンデマンドで読み込まれているため、Vspackage が読み込まれていないによって、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]デザイナーのインスタンスを作成する前に環境。 そのため、Vspackage は、処理するためには、作成時にデザイナーまたはデザイナー コンポーネントを構成するための標準メカニズムを使用できません、<xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated>イベント。 VSPackage がのインスタンスを実装する代わりに、<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>インターフェイスをデザイン画面の拡張機能と呼ばれるカスタマイズを提供できる自身を登録します。  
  
### <a name="customize-initialization"></a>初期化をカスタマイズします。  
 デザイナー、コンポーネント、またはデザイナーの画面をカスタマイズする必要があります。  
  
1. デザイナーのメタデータを変更して効果的に特定する方法を変更する<xref:System.Type>がアクセスまたは変換します。  
  
    これは、通常、<xref:System.Drawing.Design.UITypeEditor>または<xref:System.ComponentModel.TypeConverter>メカニズム。  
  
    たとえば、 <xref:System.Windows.Forms>-ベースのデザイナーを初期化すると、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境を変更します、<xref:System.Drawing.Design.UITypeEditor>の<xref:System.Web.UI.WebControls.Image>デザイナーを使用した、resource manager を使用して、ファイル システムではなく、ビットマップを取得するために使用するオブジェクト。  
  
2. イベントにサブスクライブするか、プロジェクトの構成情報を取得して、環境と統合します。 プロジェクトの構成情報を取得してイベントにサブスクライブして取得することによって、<xref:System.ComponentModel.Design.ITypeResolutionService>インターフェイス。  
  
3. 適切なライセンス認証でユーザー環境の変更**ツールボックス**カテゴリのインスタンスを適用することで、デザイナーの適用性を制限することで、<xref:System.ComponentModel.ToolboxItemFilterAttribute>デザイナー クラス。  
  
### <a name="designer-initialization-by-a-vspackage"></a>Vspackage のデザイナーの初期化  
 VSPackage は、デザイナーの初期化を処理する必要があります。  
  
1. 実装するオブジェクトを作成、<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>クラス。  
  
   > [!NOTE]
   >  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>と同じオブジェクトのクラスを実装することはありません、<xref:Microsoft.VisualStudio.Shell.Package>クラス。  
  
2. 実装するクラスを登録<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>のインスタンスを適用することで、VSPackage のデザイナーの拡張機能のサポートを提供するものとして<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>、<xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>と<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>の VSPackage の実装を提供するクラスに<xref:Microsoft.VisualStudio.Shell.Package>.  
  
   すべてのデザイナーまたはデザイナー コンポーネントを作成すると、されるたびに、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境。  
  
3. 各登録済みのデザイン画面の拡張機能のプロバイダーにアクセスします。  
  
4. インスタンス化し、各デザイン サーフェスの拡張機能プロバイダーのインスタンスを初期化します<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>オブジェクト  
  
5. デザイン画面の拡張機能プロバイダーの各を呼び出す<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>メソッドまたは<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A>メソッド (必要に応じて)。  
  
   実装する場合、 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> VSPackage のメンバーとしてオブジェクトのことを理解することが重要。  
  
6. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境はどのようなメタデータを制御を提供していないか、特定の他の構成設定`DesignSurfaceExtension`プロバイダーの変更します。 2 つ以上のことは`DesignSurfaceExtension`プロバイダーが明確にされている最後の変更を使用した、競合している方法で同じデザイナー機能を変更します。 どの変更が適用される最後は不確定はありません。  
  
7. 実装を明示的に制限することは、<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>オブジェクトのインスタンスを適用することで、特定のデザイナーを<xref:System.ComponentModel.ToolboxItemFilterAttribute>その実装にします。 詳細については**ツールボックス**フィルターの項目を参照してください、<xref:System.ComponentModel.ToolboxItemFilterAttribute>と<xref:System.ComponentModel.ToolboxItemFilterType>します。  
  
## <a name="additional-metadata-provisioning"></a>追加のメタデータのプロビジョニング  
 VSPackage では、デザイン時にデザイナーまたは以外のデザイナー コンポーネントの構成を変更できます。  
  
 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>クラスをプログラムで使用できるデザイナーを提供する VSPackage に適用することもできます。  
  
 インスタンス、<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>クラスは、デザイン サーフェイス上で作成されたコンポーネントのメタデータの変更に使用されます。 たとえば、1 つで使用される既定のプロパティ ブラウザーを置き換えることができます<xref:System.Windows.Forms.CommonDialog>カスタム プロパティ ブラウザーでのオブジェクト。  
  
 インスタンスによって提供される変更<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>の VSPackage の実装に適用される<xref:Microsoft.VisualStudio.Shell.Package>2 つのスコープのいずれかの。  
  
- 指定したコンポーネントのすべての新しいインスタンスの Global--  
  
- ローカル--現在 VSPackage によって提供されるデザイン サーフェイス上に作成されるコンポーネントのインスタンスにのみ関連します。  
  
  `IsGlobal`のプロパティ、<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>の VSPackage の実装に適用されるインスタンス<xref:Microsoft.VisualStudio.Shell.Package>このスコープを決定します。  
  
  実装に属性を適用する<xref:Microsoft.VisualStudio.Shell.Package>で、<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A>のプロパティ、<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>オブジェクトに設定して`true`、全体のブラウザーを次のように、変更[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境。  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
  グローバル フラグが設定された場合`false`メタデータの変更は、現在の VSPackage でサポートされている現在のデザイナーにローカル。  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  現時点では、デザイン画面には、コンポーネントの作成のみがサポートされ、したがってコンポーネントのみがローカルのメタデータを持つことができます。 など、プロパティの変更を試みた上記の例では、`Color`オブジェクトのプロパティ。 場合`false`、グローバル フラグの渡された`CustomBrowser`はデザイナーのインスタンスを実際に作成するためには表示されません`Color`します。 グローバル フラグを設定`false`コンポーネント、コントロール、タイマー、およびダイアログ ボックスなどの役に立ちます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [デザイン時サポートを拡張します。](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)