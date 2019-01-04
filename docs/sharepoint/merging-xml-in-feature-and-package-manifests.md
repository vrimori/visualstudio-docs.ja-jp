---
title: マニフェストの XML 機能およびパッケージのマージ |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 30c339bf38f8fc873b27b9c213fad21d66fb9fa7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914437"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>フィーチャーとパッケージ マニフェストでの XML をマージします。
  フィーチャーとパッケージがによって定義されている[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]マニフェスト ファイル。 これらのパッケージ マニフェストは生成されたデザイナーとカスタム データの組み合わせ[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]マニフェスト テンプレートにユーザーを入力します。 パッケージ実行時、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]カスタム マージ[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]ステートメントとデザイナーの[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]パッケージを形成する[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]マニフェスト ファイル。 同様の要素の例外を除き、例外のマージで後でマージを避けるために[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]、sharepoint、ファイルをデプロイすると、マニフェストを作成するファイルより小さいとより効率的に検証エラー。  
  
## <a name="modify-the-manifests"></a>マニフェストを変更します。
 フィーチャーまたはパッケージ デザイナーを無効にするまでは、パッケージ マニフェスト ファイルを直接変更することはできません。 ユーザー設定を手動で追加するただし、[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]要素マニフェスト テンプレートを機能とパッケージ デザイナーを使用するかまたは[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]エディター。 詳細については、「[方法 :SharePoint フィーチャーをカスタマイズ](../sharepoint/how-to-customize-a-sharepoint-feature.md)と[方法。SharePoint ソリューション パッケージをカスタマイズ](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)します。  
  
## <a name="feature-and-package-manifest-merge-process"></a>機能およびパッケージ マニフェストのマージ プロセス
 デザイナーが提供の要素と共にカスタム要素を結合するときに[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]は次のプロセスを使用します。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 各要素に一意のキー値があるかどうかを確認します。 一意のキー値を持つ要素がない場合は、パッケージ マニフェスト ファイルに追加されます。 同様に、複数のキーを持つ要素をマージできません。 そのため、マニフェスト ファイルに、それらが追加されます。  
  
 要素に一意のキーが[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]デザイナーとカスタムのキーの値を比較します。 値が一致した場合、単一の値にマージします。 値が異なる場合、デザイナーのキー値が破棄され、カスタムのキー値が使用されます。 コレクションもマージされます。 たとえば場合、デザイナーで生成された[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]にカスタム[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]両方のアセンブリのコレクションを含めることが、パッケージ マニフェストには、1 つだけのアセンブリのコレクションが含まれています。  
  
## <a name="merge-exceptions"></a>例外をマージします。
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ほとんどのデザイナーをマージ[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]要素および同様のカスタム[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]要素の 1 つの一意の識別属性がある限りです。 ただし、必要な一意の識別子のないいくつかの要素[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]マージします。 これらの要素と呼ばれる*例外をマージ*します。 このような場合は、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]カスタム マージしない[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]要素およびデザイナーの[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]要素が代わりにそれらをパッケージ マニフェスト ファイルに追加されます。  
  
 機能およびパッケージのマージの例外の一覧を次に[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]マニフェスト ファイル。  
  
|Designer|XML 要素|  
|--------------|-----------------|  
|フィーチャー デザイナー|ActivationDependency|  
|フィーチャー デザイナー|UpgradeAction|  
|パッケージ デザイナー|SafeControl|  
|パッケージ デザイナー|CodeAccessSecurity|  
  
## <a name="feature-manifest-elements"></a>フィーチャー マニフェスト要素
 次の表では、マージできるすべての機能のマニフェスト要素と、その照合に使用される一意キーの一覧を示します。  
  
|要素名|一意のキー|  
|------------------|----------------|  
|機能 (すべての属性)|*属性名*(機能の要素の各属性名は一意のキーです)。|  
|ElementFile|場所|  
|ElementManifests/ElementManifest|場所|  
|プロパティ/プロパティ|キー|  
|CustomUpgradeAction|名前|  
|CustomUpgradeActionParameter|名前|  
  
> [!NOTE]  
>  CustomUpgradeAction 要素を変更する唯一の方法が、カスタムのため、[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]エディター、いないをマージした効果が低い。  
  
## <a name="package-manifest-elements"></a>パッケージ マニフェスト要素
 次の表では、マージ可能なすべてのパッケージ マニフェスト要素とその照合に使用される一意キーの一覧を示します。  
  
|要素名|一意のキー|  
|------------------|----------------|  
|ソリューション (すべての属性)|*属性名*(ソリューションの要素の各属性名は一意のキーです)。|  
|ApplicationResourceFiles/ApplicationResourceFile|場所|  
|アセンブリ/アセンブリ|場所|  
|ClassResources/ClassResource|場所|  
|DwpFiles/DwpFile|場所|  
|FeatureManifests/FeatureManifest|場所|  
|リソース/リソース|場所|  
|RootFiles/RootFile|場所|  
|SiteDefinitionManifests/SiteDefinitionManifest|場所|  
|WebTempFile|場所|  
|TemplateFiles/TemplateFile|場所|  
|SolutionDependency|SolutionID|  
  
## <a name="manually-add-deployed-files"></a>配置済みのファイルを手動で追加します。
 ApplicationResourceFile DwpFiles などのいくつかのマニフェスト要素は、ファイル名が含まれている場所を指定します。 ただし、マニフェスト テンプレートへのファイル名のエントリの追加はない基になるファイル パッケージに追加します。 パッケージに含めるし、その展開の種類プロパティを適宜設定をプロジェクトにファイルを追加する必要があります。  
  
## <a name="see-also"></a>関連項目
 [パッケージ化し、SharePoint ソリューションのデプロイ](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [SharePoint ソリューションのビルドとデバッグ](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
