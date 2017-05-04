---
title: "フィーチャー マニフェストとパッケージ マニフェストの XML のマージ | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio での SharePoint 開発, パッケージ化"
ms.assetid: fc1cbd2a-0166-4f2f-a81b-4dac2fa7b0f3
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# フィーチャー マニフェストとパッケージ マニフェストの XML のマージ
  フィーチャーとパッケージは、[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] マニフェスト ファイルによって定義されます。  それらのパッケージ化されたマニフェストには、デザイナーから生成されたデータと、ユーザーがマニフェスト テンプレートに入力したカスタム [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] が組み合わされています。  パッケージ化の際に、カスタム [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ステートメントがデザイナー生成の [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] とマージされて、パッケージ化された [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] マニフェスト ファイルが作成されます。  同等の要素をマージすることにより \(例外については後の「マージの例外」を参照\)、ファイルを SharePoint に配置した後に [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 検証エラーが発生するのを防ぎ、マニフェスト ファイルをより小さく効率的なものにすることができます。  
  
## マニフェストの変更  
 パッケージ化されたマニフェスト ファイルを直接変更するには、フィーチャー デザイナーやパッケージ デザイナーを無効にする必要があります。  ただし、マニフェスト テンプレートに手動でカスタム [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 要素を追加するには、フィーチャー デザイナーやパッケージ デザイナーを使用することも、[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] エディターを使用することもできます。  詳細については、「[方法: SharePoint フィーチャーをカスタマイズする](../sharepoint/how-to-customize-a-sharepoint-feature.md)」および「[方法: SharePoint ソリューション パッケージをカスタマイズする](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)」を参照してください。  
  
## フィーチャー マニフェストとパッケージ マニフェストのマージ プロセス  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] でカスタム要素とデザイナー生成の要素が組み合わされるプロセスでは、  まず、各要素に一意キーの値があるかどうかがチェックされます。  一意キーの値がない要素、パッケージ化されたマニフェスト ファイルの末尾に追加されます。  同様に、複数のキーを持つ要素がマージできません。  マニフェスト ファイルの末尾に追加されます。  
  
 一意キーがある要素については、デザイナー キーとカスタム キーの値が比較されて、  値が一致する場合は 1 つの値にマージされます。  値が一致しない場合は、デザイナー キーの値が破棄されて、カスタム キーの値が使用されます。  コレクションもマージされます。  たとえば、デザイナー生成の [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] とカスタム [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] の両方に Assemblies コレクションが含まれている場合、パッケージ化されたマニフェストには Assemblies コレクションが 1 つだけ含まれます。  
  
## マージの例外  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] では、一意の識別属性を 1 つだけ持っている限り、ほとんどのデザイナー [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 要素が同等のカスタム [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 要素とマージされます。  しかし、[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] のマージに必要な一意識別子を持たない要素もあります。  それらの要素を、*マージの例外*と呼びます。  これらの要素は、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] によるカスタム [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 要素とデザイナー生成の [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 要素のマージの対象にならず、パッケージ化されたマニフェスト ファイルの末尾に追加されます。  
  
 次の表に、フィーチャーとパッケージの [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] マニフェスト ファイルのマージの例外を示します。  
  
|デザイナー|XML 要素|  
|-----------|------------|  
|フィーチャー デザイナー|ActivationDependency|  
|フィーチャー デザイナー|UpgradeAction|  
|パッケージ デザイナー|SafeControl|  
|パッケージ デザイナー|CodeAccessSecurity|  
  
## フィーチャー マニフェスト要素  
 次の表は、マージできるフィーチャー マニフェスト要素と、その照合に使用される一意キーの一覧です。  
  
|要素名|一意キー|  
|---------|----------|  
|Feature \(すべての属性\)|*Attribute Name* \(Feature 要素の各属性名が一意キーです\)|  
|ElementFile|場所|  
|ElementManifests\/ElementManifest|場所|  
|Properties\/Property|キー|  
|CustomUpgradeAction|名前|  
|CustomUpgradeActionParameter|名前|  
  
> [!NOTE]  
>  CustomUpgradeAction 要素はカスタム [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] エディターでしか変更できないため、マージされなくても大きな影響はありません。  
  
## パッケージ マニフェスト要素  
 次の表は、マージできるパッケージ マニフェスト要素と、その照合に使用される一意キーの一覧です。  
  
|要素名|一意キー|  
|---------|----------|  
|Solution \(すべての属性\)|*Attribute Name* \(ソリューション要素の各属性名が一意キーです\)|  
|ApplicationResourceFiles\/ApplicationResourceFile|場所|  
|Assemblies\/Assembly|場所|  
|ClassResources\/ClassResource|場所|  
|DwpFiles\/DwpFile|場所|  
|FeatureManifests\/FeatureManifest|場所|  
|Resources\/Resource|場所|  
|RootFiles\/RootFile|場所|  
|SiteDefinitionManifests\/SiteDefinitionManifest|場所|  
|WebTempFile|場所|  
|TemplateFiles\/TemplateFile|場所|  
|SolutionDependency|SolutionID|  
  
## 配置ファイルの手動による追加  
 ファイル名を含む場所を指定するマニフェスト要素もありますが \(ApplicationResourceFile、DwpFiles など\)、  マニフェスト テンプレートにファイル名のエントリを追加しても、基になるファイルはパッケージに追加されません。  ファイルをパッケージに含めるには、そのファイルをプロジェクトに追加して、\[配置タイプ\] プロパティを設定する必要があります。  
  
## 参照  
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [SharePoint ソリューションのビルドとデバッグ](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  