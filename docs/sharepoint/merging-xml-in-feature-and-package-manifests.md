---
title: "マニフェストに機能およびパッケージ XML のマージ |Microsoft ドキュメント"
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
helpviewer_keywords: SharePoint development in Visual Studio, packaging
ms.assetid: fc1cbd2a-0166-4f2f-a81b-4dac2fa7b0f3
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 895bb4f7bde787a135699e4197622037413a1869
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="merging-xml-in-feature-and-package-manifests"></a>フィーチャー マニフェストとパッケージ マニフェストの XML のマージ
  フィーチャーとパッケージがによって定義されている[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]マニフェスト ファイル。 これらのパッケージのマニフェストは、デザイナーとカスタムから生成されたデータの組み合わせ[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]ユーザーによって、マニフェスト テンプレートに入力します。 パッケージ実行時、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]カスタムをマージ[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]ステートメントと、デザイナーによって提供された[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]、パッケージを形成する[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]マニフェスト ファイル。 ような要素は、後でマージの例外を示すような例外がマージを回避する[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]検証エラーの後、SharePoint にファイルを展開して、マニフェストを作成するファイルより小さい方が効率的です。  
  
## <a name="modifying-the-manifests"></a>マニフェストの変更  
 フィーチャーまたはパッケージ デザイナーを無効にするまでは、パッケージ マニフェスト ファイルを直接変更することはできません。 、ユーザーが手動で追加することができます[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]要素マニフェスト テンプレートに機能およびパッケージ デザイナーを使用するか、または[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]エディターです。 詳細については、次を参照してください。[する方法: SharePoint フィーチャーをカスタマイズ](../sharepoint/how-to-customize-a-sharepoint-feature.md)と[する方法: SharePoint ソリューション パッケージをカスタマイズ](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)です。  
  
## <a name="feature-and-package-manifest-merge-process"></a>フィーチャーとパッケージ マニフェストのマージ プロセス  
 デザイナーが提供の要素と共にカスタム要素を結合するときに[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]は次のプロセスを使用します。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]各要素に一意のキー値があるかどうかを確認します。 要素に一意のキー値があるない場合は、パッケージ マニフェスト ファイルに追加されます。 同様に、複数のキーを持つ要素をマージすることはできません。 そのため、マニフェスト ファイルに、これらは追加されます。  
  
 要素に一意のキーが[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]デザイナーとカスタムのキーの値を比較します。 値が一致した場合は、単一の値にそれらをマージします。 値が異なる場合、デザイナーのキーの値が破棄され、カスタムのキーの値を使用します。 コレクションもマージされます。 たとえば場合、デザイナーで生成された[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]とカスタム[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]両方のアセンブリ コレクションを含む、パッケージのマニフェストには、1 つだけのアセンブリのコレクションが含まれています。  
  
## <a name="merge-exceptions"></a>マージの例外  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ほとんどのデザイナーをマージ[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]要素および同様のカスタム[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]要素の 1 つの一意の識別属性がある限りです。 いくつかの要素に必要な一意の識別子が不足しているただし、[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]をマージします。 これらの要素と呼ばれる*例外をマージ*です。 このような場合は、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]カスタムをマージしません[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]要素と共に、デザイナーによって提供された[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]要素が、代わりに、パッケージ マニフェスト ファイルに追加します。  
  
 次の機能およびパッケージのマージの例外の一覧は[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]マニフェスト ファイル。  
  
|Designer|XML 要素|  
|--------------|-----------------|  
|フィーチャー デザイナー|ActivationDependency|  
|フィーチャー デザイナー|UpgradeAction|  
|パッケージ デザイナー|SafeControl|  
|パッケージ デザイナー|CodeAccessSecurity|  
  
## <a name="feature-manifest-elements"></a>フィーチャー マニフェスト要素  
 次の表は、マージできるすべてのフィーチャー マニフェスト要素とその照合に使用される一意キーの一覧を示します。  
  
|要素名|一意のキー|  
|------------------|----------------|  
|機能 (すべての属性)|*属性名*(機能の要素のそれぞれの属性名は一意のキーです)。|  
|ElementFile|場所|  
|ElementManifests/ElementManifest|場所|  
|プロパティ/プロパティ|キー|  
|CustomUpgradeAction|name|  
|CustomUpgradeActionParameter|name|  
  
> [!NOTE]  
>  CustomUpgradeAction 要素を変更する唯一の方法がカスタムであるため[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]エディター、いないをマージした効果が不足します。  
  
## <a name="package-manifest-elements"></a>パッケージ マニフェストの要素  
 次の表は、マージできるすべてのパッケージ マニフェスト要素とその照合に使用される一意キーの一覧を示します。  
  
|要素名|一意のキー|  
|------------------|----------------|  
|ソリューション (すべての属性)|*属性名*(ソリューションの要素のそれぞれの属性名は一意のキーです)。|  
|ApplicationResourceFiles/ApplicationResourceFile|場所|  
|アセンブリ/アセンブリ|場所|  
|ClassResources/ClassResource|場所|  
|DwpFiles/DwpFile|場所|  
|FeatureManifests/FeatureManifest|場所|  
|リソース/リソース|場所|  
|フォルダー/RootFile|場所|  
|SiteDefinitionManifests/SiteDefinitionManifest|場所|  
|WebTempFile|場所|  
|TemplateFiles/TemplateFile|場所|  
|SolutionDependency|ソリューション Id|  
  
## <a name="manually-add-deployed-files"></a>配置済みのファイルを手動で追加します。  
 ApplicationResourceFile DwpFiles などのいくつかのマニフェスト要素は、ファイル名を含む場所を指定します。 ただし、マニフェスト テンプレートへのファイル名のエントリを追加できません、基になるファイルに追加されませんパッケージです。 パッケージに含めるし、その展開の種類プロパティを適宜設定をプロジェクトにファイルを追加する必要があります。  
  
## <a name="see-also"></a>参照  
 [パッケージ化と SharePoint ソリューションの配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [SharePoint ソリューションのビルドとデバッグ](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  