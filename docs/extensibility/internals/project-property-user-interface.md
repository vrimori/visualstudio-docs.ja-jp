---
title: プロジェクトのプロパティのユーザー インターフェイス |Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ec1a46b619eecc08e08c74535430f9a0d7bfc3c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957055"
---
# <a name="project-property-user-interface"></a>プロジェクト プロパティのユーザー インターフェイス
プロジェクト サブタイプは、プロジェクトで項目を使用できる**プロパティ ページ** ダイアログ ボックス ベースのプロジェクトで指定されているように非表示または読み取り専用のコントロールとページ全体のことを指定するには、または、にプロジェクトサブタイプに固有のページを追加**プロパティ ページ** ダイアログ ボックス。

## <a name="extending-the-project-property-dialog-box"></a>プロジェクトのプロパティ ダイアログ ボックスを拡張します。
 プロジェクト サブタイプは、オートメーション エクステンダーとプロジェクト構成の参照オブジェクトを実装します。 これらのエクステンダーの実装、<xref:EnvDTE.IFilterProperties>インターフェイスの特定のプロパティを非表示] または [読み取り専用にします。 **プロパティ ページ**ベースのプロジェクトによって実装される、基本プロジェクトのダイアログ ボックスでは、オートメーション エクステンダーによって実行されるフィルター処理します。

 拡張するプロセス、**プロジェクト プロパティ** ダイアログ ボックスを以下に示します。

-   ベースのプロジェクトからプロジェクトのサブタイプが実装することによって、エクステンダーを取得する、<xref:EnvDTE80.IInternalExtenderProvider>インターフェイス。 [参照]、プロジェクトの自動化、およびすべての基本プロジェクトのプロジェクト構成の参照オブジェクトは、このインターフェイスを実装します。

-   実装<xref:EnvDTE80.IInternalExtenderProvider>にプロジェクトの参照オブジェクトとプロジェクト オートメーション オブジェクトがデリゲート用、<xref:EnvDTE80.IInternalExtenderProvider>プロジェクト サブタイプのアグリゲーターの実装 (つまり、これら`QueryInterface`の<xref:EnvDTE80.IInternalExtenderProvider>で、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>プロジェクトのオブジェクトの場合)。

-   基本プロジェクト構成の参照オブジェクトも実装<xref:EnvDTE80.IInternalExtenderProvider>プロジェクト サブタイプの構成オブジェクトからオートメーション エクステンダーに直接接続する機能。 その実装のデリゲートを<xref:EnvDTE80.IInternalExtenderProvider>プロジェクト サブタイプのアグリゲーターによって実装されるインターフェイス。

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>、プロジェクト構成参照オブジェクトを返します。 によって実装される、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>オブジェクト。

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>、プロジェクト構成参照オブジェクトを返します。 によって実装されることも、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>オブジェクト。

-   プロジェクト サブタイプであるか、次を取得することによって実行時に基本プロジェクトのさまざまな拡張可能なオブジェクトの適切な Catid を調べる<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>値。

    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

プロジェクト サブタイプ プロジェクト スコープの Catid を判断するには上記のプロパティを取得します[VSITEMID します。ルート](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)から、`VSITEMID typedef`します。 プロジェクト サブタイプを制御する可能性がありますも**プロパティ ページ**プロジェクトのダイアログ ボックスのページが表示されます構成に依存し、構成に依存しません。 いくつかのプロジェクト サブタイプは、組み込みのページを削除し、プロジェクトのサブタイプの特定のページを追加する必要があります。 この管理対象のクライアント プロジェクトの呼び出しを有効にするには、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>メソッドは、次のプロパティ。

-   `VSHPROPID_PropertyPagesCLSIDList` 構成に依存しないプロパティ ページの Clsid のセミコロン区切りのリスト。

-   `VSHPROPID_CfgPropertyPagesCLSIDList —` 構成に依存するプロパティ ページの Clsid のセミコロン区切りのリスト。

プロジェクト サブタイプの集計であるため、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>オブジェクト、これを制御するこれらのプロパティの定義をオーバーライドできます**プロパティ ページ** ダイアログ ボックスが表示されます。 プロジェクト サブタイプ内部の基本プロジェクトからこれらのプロパティを取得し、し、追加または削除できます Clsid に応じて。

プロジェクト サブタイプによって追加された新しいプロパティ ページには、プロジェクトの基本実装からプロジェクト構成の参照オブジェクトが渡されます。 このプロジェクト構成の参照オブジェクトには、オートメーション エクステンダーがサポートしています。 AutomationExtenders の詳細については、次を参照してください。[実装とオートメーション エクステンダーを使用して](https://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356)します。 プロジェクト サブタイプの呼び出しによって実装されるプロパティ ページ<xref:EnvDTE.Project.Extender%2A>オブジェクトを取得する独自プロジェクト サブタイプ構成参照ベースのプロジェクトの構成の参照オブジェクトを拡張します。

## <a name="see-also"></a>関連項目

- <xref:EnvDTE.IFilterProperties>
- [プロパティ ページ ダイアログ ボックス](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))