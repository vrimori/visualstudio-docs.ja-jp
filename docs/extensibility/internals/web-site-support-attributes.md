---
title: Web サイト サポートの属性 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ea55937318d22a40b90cddb54490b87ab0c44325
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916823"
---
# <a name="web-site-support-attributes"></a>Web サイト サポートの属性
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Web サイト プロジェクトは、プログラミング言語の Web サポートを提供する拡張できます。 言語には、自らを登録する必要があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]にプロジェクト テンプレートが表示できるように、**新しい Web サイト**ダイアログ ボックスの言語が選択されているとします。

IronPython Studio サンプルには、web サイトのサポートが含まれています。 このサンプルには、IronPython を新しい Web プロジェクトの分離コードの言語として登録する次の属性クラスが含まれています。

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 この属性は、言語のプロジェクトに配置されます。 Web でのプログラミング言語の一覧に、言語を追加、**言語**の一覧で、**新しい Web サイト** ダイアログ ボックス。 たとえば、次のコードでは、一覧に IronPython を追加します。

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 この属性は、またテンプレート フォルダーをポイントするテンプレートのパスを設定します。 テンプレート フォルダーの場所の詳細については、次を参照してください。 [Web サイトのサポート テンプレート](../../extensibility/internals/web-site-support-templates.md)します。

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 この属性は、言語のプロジェクトに配置されます。 別のファイルの種類 (プライマリ) (関連) 1 つのファイルの種類を入れ子にする Web サイト プロジェクトのできる、**ソリューション エクスプ ローラー**します。

 たとえば、次のコードでは、IronPython の分離コード ファイルが .aspx ファイルに関連することを指定します。 IronPython の Web サイト ソリューションで新しい .aspx Web ページが作成されると、新しい .py ソース ファイルが生成され、.aspx ページの子ノードとして表示されます。

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 この属性は、言語のプロジェクトのパッケージに配置されます。 言語の IntelliSense のプロバイダーを選択します。

 たとえば、次のコードを指定する PythonIntellisenseProvider で、実装のインスタンス<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>、言語サービスを提供するオンデマンドで作成する必要があります。

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 IVsIntellisenseProject 実装では、参照を処理し、コードを含む Web ページを要求したがキャッシュされていないときに、言語コンパイラを呼び出します。

## <a name="see-also"></a>関連項目
 [Web サイト サポート](../../extensibility/internals/web-site-support.md)