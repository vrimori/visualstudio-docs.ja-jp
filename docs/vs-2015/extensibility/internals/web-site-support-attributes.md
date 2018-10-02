---
title: Web サイト サポートの属性 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3fd60c1ffcb6bb4d3c386cf55fb1f33540bb3dd2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547262"
---
# <a name="web-site-support-attributes"></a>Web サイト サポートの属性
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Web サイト サポート属性](https://docs.microsoft.com/visualstudio/extensibility/internals/web-site-support-attributes)します。  
  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Web サイト プロジェクトは、プログラミング言語の Web サポートを提供する拡張できます。 言語には、自らを登録する必要があります[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]にプロジェクト テンプレートが表示できるように、**新しい Web サイト**ダイアログ ボックスの言語が選択されているとします。  
  
 IronPython Studio サンプルには、web サイトのサポートが含まれています。 それを見つけることができます、 [VSSDK のサンプル](../../misc/vssdk-samples.md)します。 新しい Web プロジェクトの分離コードの言語として IronPython を登録する次の属性クラスが含まれています。  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 この属性は、言語のプロジェクトに配置されます。 Web でのプログラミング言語の一覧に、言語を追加、**言語**の一覧で、**新しい Web サイト** ダイアログ ボックス。 たとえば、次の IronPython 一覧に追加します。  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 この属性は、またテンプレート フォルダーをポイントするテンプレートのパスを設定します。 テンプレート フォルダーの場所の詳細については、次を参照してください。 [Web サイトのサポート テンプレート](../../extensibility/internals/web-site-support-templates.md)します。  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 この属性は、言語のプロジェクトに配置されます。 別のファイルの種類 (プライマリ) (関連) 1 つのファイルの種類を入れ子にする Web サイト プロジェクトのできる、**ソリューション エクスプ ローラー**します。  
  
 例えば:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 IronPython の分離コード ファイルが .aspx ファイルに関連することを指定します。 IronPython の Web サイト ソリューションで新しい .aspx Web ページが作成されると、新しい .py ソース ファイルが生成され、.aspx ページの子ノードとして表示されます。  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 この属性は、言語のプロジェクトのパッケージに配置されます。 言語の Intellisense のプロバイダーを選択します。  
  
 例えば:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 指定します、PythonIntellisenseProvider 実装のインスタンス<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>、言語サービスを提供するオンデマンドで作成する必要があります。  
  
 IVsIntellisenseProject 実装では、参照を処理し、コードを含む Web ページを要求したがキャッシュされていないときに、言語コンパイラを呼び出します。  
  
## <a name="see-also"></a>関連項目  
 [Web サイト サポート](../../extensibility/internals/web-site-support.md)

