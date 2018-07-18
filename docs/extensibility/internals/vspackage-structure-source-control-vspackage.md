---
title: VSPackage 構造 (ソース管理 VSPackage) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d36e31db9c47325e62fe759cd5030c5f24fb73be
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057624"
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage 構造 (ソース管理 VSPackage)

ソース コントロールのパッケージの SDK では、VSPackage を作成するためのガイドラインにより、自分のソース管理機能を Visual Studio 環境と統合するソース コントロールの実行者を提供します。 VSPackage は、そのレジストリ エントリで、パッケージによって提供されているサービスの Visual Studio 統合開発環境 (IDE) によって、オンデマンドで読み込まれる通常 COM コンポーネントです。 すべての VSPackage を実装する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>します。 VSPackage は通常、Visual Studio IDE によって提供されるサービスを利用して、proffers、独自の一部のサービス。

VSPackage では、そのメニュー項目を宣言し、.vsct ファイルを使用して既定の項目の状態を確立します。 Visual Studio IDE では、VSPackage が読み込まれるまで、この状態で、メニュー項目が表示されます。 その後、VSPackage の実装の<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>を有効にするか、メニュー項目を無効にするメソッドが呼び出されます。

## <a name="source-control-package-characteristics"></a>ソース コントロール パッケージの特性

ソース管理 VSPackage は Visual Studio に緊密に統合します。 VSPackage のセマンティクスは次のとおりです。

-   あること、VSPackage によって実装されるインターフェイス (、`IVsPackage`インターフェイス)

-   UI コマンドの実装 (.vsct ファイルとの実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイス)

-   Visual Studio を使用した VSPackage の登録。

ソース管理 VSPackage は、これら他の Visual Studio のエンティティと通信する必要があります。

-   プロジェクト

-   エディター

-   ソリューション

-   Windows

-   実行中の document テーブル

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>使用できる visual Studio 環境のサービス

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

SVsRegisterScciProvider サービス

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>VSIP インターフェイス実装され、呼び出されます

ソース管理のパッケージは、VSPackage とその他の Visual Studio に登録されている Vspackage と直接やり取りできるためです。 ソース管理機能一式を提供するためにソース管理 VSPackage 扱うことができるプロジェクトまたはシェルによって提供されるインターフェイス。

Visual Studio ですべてのプロジェクトを実装する必要があります、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> Visual Studio IDE 内のプロジェクトとして認識されるようにします。 ただし、このインターフェイスがない特殊化されたソース管理には十分です。 ソースの下に必要なプロジェクト管理の実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>します。 このインターフェイスは、その内容にプロジェクトを照会して、グリフとバインディング情報 (必要な情報、サーバーの場所とディスクの場所の下にあるプロジェクトの間の接続を確立するために提供することをソース管理 VSPackage によって使用されます。ソース管理の場合)。

ソース管理 VSPackage の実装、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>、さらにプロジェクトをソース管理に登録し、その状態のグリフを取得できます。

ソース管理 VSPackage が考慮する必要があるインターフェイスの完全な一覧を参照してください。[関連サービスとインターフェイス](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)します。

## <a name="see-also"></a>関連項目

- [デザイン要素](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [関連サービスとインターフェイス](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)