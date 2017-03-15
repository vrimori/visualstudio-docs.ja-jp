---
title: "Web サイトのサポート属性 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 9
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: dba1aeb8f8e3ad368f050ef425f76cc6c94f99e8
ms.lasthandoff: 02/22/2017

---
# <a name="web-site-support-attributes"></a>Web サイトのサポートの属性
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Web サイト プロジェクトは、プログラミング言語サポートするため、Web に拡張できます。 言語には、自分自身を登録する必要があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクト テンプレートに入力できるように、**新しい Web サイト** ダイアログ ボックスの言語を選択するとします。  
  
 IronPython Studio サンプルには、web サイトのサポートが含まれています。 それを見つけたら、 [VSSDK サンプル](../../misc/vssdk-samples.md)します。 新規の Web プロジェクトの分離コードの言語として IronPython を登録する次の属性クラスが含まれています。  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 この属性は、言語のプロジェクトに配置されます。 Web プログラミングの言語の一覧に、言語を追加、**言語**リストに、**新しい Web サイト** ダイアログ ボックス。 たとえば、次 IronPython リストに追加します。  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 この属性は、また、テンプレート フォルダーをポイントするテンプレートのパスを設定します。 テンプレート フォルダーの場所の詳細については、次を参照してください。[サポートの Web サイト テンプレート](../../extensibility/internals/web-site-support-templates.md)します。  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 この属性は、言語のプロジェクトに配置されます。 できます (関連)。&1; つのファイルの種類の入れ子にする Web サイト プロジェクト別のファイル形式 (プライマリ) の下で、**ソリューション エクスプ ローラー**します。  
  
 例:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 IronPython の分離コード ファイルが .aspx ファイルに関連することを指定します。 IronPython Web サイト ソリューションで新しい .aspx Web ページが作成されると、新しい .py ソース ファイルが生成され、.aspx ページの子ノードとして表示されます。  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 この属性は、言語のプロジェクトのパッケージに配置されます。 言語の Intellisense のプロバイダーを選択します。  
  
 例:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 指定する PythonIntellisenseProvider で、実装のインスタンス<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>、言語サービスを提供するオンデマンドで作成する必要があります</xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>。  
  
 IVsIntellisenseProject 実装では、参照を処理し、コードを含む Web ページが要求されても、キャッシュされていないときに、言語コンパイラを呼び出します。  
  
## <a name="see-also"></a>関連項目  
 [Web サイトのサポート](../../extensibility/internals/web-site-support.md)
