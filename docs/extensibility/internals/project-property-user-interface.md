---
title: プロジェクトのプロパティ ユーザー インターフェイス |Microsoft ドキュメント
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 788107666f8103a77753b93fa7c1febc73f9b97f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132428"
---
# <a name="project-property-user-interface"></a>プロジェクト プロパティのユーザー インターフェイス
プロジェクトのサブタイプは、プロジェクトで項目を使用できる**プロパティ ページ** ダイアログ ボックスは基本のプロジェクトで指定できるように非表示にするように指定すると、読み取り専用のコントロールと全体のページを作成または、にプロジェクトのサブタイプに固有のページを追加**プロパティ ページ** ダイアログ ボックス。

## <a name="extending-the-project-property-dialog-box"></a>プロジェクトのプロパティ ダイアログ ボックスを拡張します。
 プロジェクトのサブタイプは、オートメーション エクステンダーとプロジェクト構成の参照オブジェクトを実装します。 これらのエクステンダーを実装、<xref:EnvDTE.IFilterProperties>インターフェイスを非表示または読み取り専用の特定のプロパティを作成します。 **プロパティ ページ**ベースのプロジェクトでは、実装、基本プロジェクトのダイアログ ボックスでは、オートメーション エクステンダーで実行されるフィルター処理します。

 拡張するためのプロセス、**プロジェクト プロパティ** ダイアログ ボックスを以下に示します。

-   基本プロジェクトがプロジェクトのサブタイプから実装することによって、extender を取得、<xref:EnvDTE80.IInternalExtenderProvider>インターフェイスです。 [参照]、プロジェクトの自動化、およびすべての基本プロジェクトのプロジェクト構成の参照オブジェクトは、このインターフェイスを実装します。

-   実装<xref:EnvDTE80.IInternalExtenderProvider>プロジェクト参照オブジェクトと、プロジェクトのオートメーション オブジェクトにデリゲートを<xref:EnvDTE80.IInternalExtenderProvider>プロジェクト サブタイプ アグリゲーターの実装 (つまり、これら`QueryInterface`の<xref:EnvDTE80.IInternalExtenderProvider>で、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>プロジェクト オブジェクト) です。

-   基本プロジェクト構成の参照オブジェクトも実装されて<xref:EnvDTE80.IInternalExtenderProvider>プロジェクト サブタイプ構成オブジェクトからオートメーション エクステンダーで直接接続するためです。 その実装を委任する場合、<xref:EnvDTE80.IInternalExtenderProvider>プロジェクト サブタイプ アグリゲーターによって実装されるインターフェイス。

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>、プロジェクト構成参照オブジェクトを返しますによって実装される、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>オブジェクト。

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>、プロジェクト構成参照オブジェクトを返しますによる実装も、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>オブジェクト。

-   プロジェクトのサブタイプは、次を取得することによって実行時に基本プロジェクトのさまざまな拡張可能オブジェクトの適切な Catid を決定することができます<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>値。

    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

プロジェクト スコープの Catid を判断するには、プロジェクトのサブタイプ プロパティを取得します上記の[VSITEMID です。ルート](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)から、`VSITEMID typedef`です。 プロジェクトのサブタイプが制御をすることも**プロパティ ページ**プロジェクトのダイアログ ボックスのページが表示されます両方の構成に依存して構成に依存しません。 いくつかのプロジェクト サブタイプは、組み込みのページを削除し、プロジェクトのサブタイプの特定のページを追加する必要があります。 これには、管理されたクライアント プロジェクトの呼び出しを有効にするために、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>メソッドは、次のプロパティ。

-   `VSHPROPID_PropertyPagesCLSIDList` — の構成に依存しないプロパティ ページの Clsid をセミコロンで区切られた一覧です。

-   `VSHPROPID_CfgPropertyPagesCLSIDList —` 構成に依存するプロパティ ページの Clsid をセミコロンで区切った一覧。

プロジェクトのサブタイプの集計のため、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>オブジェクトを制御するこれらのプロパティの定義をオーバーライドできます**プロパティ ページ** ダイアログ ボックスが表示されます。 プロジェクトのサブタイプ内部の基本プロジェクトからこれらのプロパティを取得し、し、追加または削除できます Clsid 必要に応じて、します。

プロジェクトのサブタイプによって追加された新しいプロパティ ページには、基本プロジェクト実装からプロジェクト構成の参照オブジェクトが渡されます。 このプロジェクト構成の参照オブジェクトには、オートメーション エクステンダーがサポートしています。 AutomationExtenders の詳細については、次を参照してください。[実装と管理を使用してオートメーション エクステンダー](http://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356)です。 プロジェクトのサブタイプ呼び出しによって実装されたプロパティ ページ<xref:EnvDTE.Project.Extender%2A>オブジェクトを取得する独自プロジェクト サブタイプ構成参照ベースのプロジェクトの構成の参照オブジェクトを拡張します。

## <a name="see-also"></a>関連項目

- <xref:EnvDTE.IFilterProperties>
- [プロパティ ページ ダイアログ ボックス](http://msdn.microsoft.com/en-us/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)