---
title: "Web サイト サポート属性 |Microsoft ドキュメント"
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
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 66e9dcfd511a95ce1ea27af64a3a7f8302fe2827
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2018
---
# <a name="web-site-support-attributes"></a>Web サイトのサポートの属性
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Web サイト プロジェクトは、プログラミング言語の Web サポートを提供する拡張できます。 言語には、自らを登録する必要があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]でプロジェクト テンプレートが表示できるように、**新しい Web サイト**ダイアログ ボックスの言語が選択されているとします。

IronPython Studio サンプルには、web サイトのサポートが含まれています。 このサンプルには、新しい Web プロジェクトの分離コード言語として IronPython を登録する次の属性クラスが含まれています。

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 この属性は、言語のプロジェクトに配置されます。 Web プログラミングの言語の一覧に、言語を追加、**言語**一覧に、**新しい Web サイト** ダイアログ ボックス。 たとえば、次のコードでは、一覧に IronPython を追加します。

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 この属性は、また、テンプレート フォルダーをポイントするテンプレートのパスを設定します。 テンプレート フォルダーの場所の詳細については、次を参照してください。 [Web サイトのサポート テンプレート](../../extensibility/internals/web-site-support-templates.md)です。

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 この属性は、言語のプロジェクトに配置されます。 これにより、(関連) 1 つのファイルの種類の入れ子に Web サイト プロジェクト別のファイル種類 (プライマリ) の下で、**ソリューション エクスプ ローラー**です。

 たとえば、次のコードでは、IronPython 分離コード ファイルを .aspx ファイルに関連することを指定します。 IronPython の Web サイト ソリューションに新しい .aspx Web ページが作成されると、新しい .py ソース ファイルが生成され、.aspx ページの子ノードとして表示されます。

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 この属性は、言語のプロジェクトのパッケージに配置されます。 言語の IntelliSense プロバイダーを選択します。

 たとえば、次のコードを指定するを実装する PythonIntellisenseProvider インスタンス<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>、言語サービスを提供するオンデマンドで作成する必要があります。

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 IVsIntellisenseProject 実装では、参照を処理し、コードを含む Web ページが要求されましたが、キャッシュされていないときに、言語コンパイラを呼び出します。

## <a name="see-also"></a>参照
 [Web サイト サポート](../../extensibility/internals/web-site-support.md)