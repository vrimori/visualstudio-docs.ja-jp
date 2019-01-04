---
title: 言語に含まれている |Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce2079ce16ac339ae536430d02d546ea39ffae0a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53874003"
---
# <a name="contained-languages"></a>含まれている言語

*言語に含まれている*は他の言語に含まれている言語。 たとえば、HTML で[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]ページに含めることができます[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]または[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]スクリプト。 デュアル言語アーキテクチャが必要です、 *.aspx* IntelliSense、色付け、およびその他の編集を提供するファイルのエディターは、HTML とスクリプト言語の両方に機能します。

## <a name="implementation"></a>実装

含まれている言語を実装する必要がある最も重要なインターフェイスは、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>インターフェイス。 このインターフェイスは、主言語内でホストされる任意の言語によって実装されます。 言語サービスの colorizer、テキスト ビューのフィルター、およびプライマリ言語サービスの ID にアクセスします。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>を作成することができます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>インターフェイス。 次の手順では、含まれている言語を実装する方法を示します。

1.  使用`QueryService()`言語サービスの ID とのインターフェイス ID を取得する、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>します。

2.  作成する、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>インターフェイスを呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A>メソッド。 渡す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>インターフェイス、1 つまたは複数[項目の Id](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>)、および<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>インターフェイス。

3.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>テキスト バッファーのコーディネーター オブジェクトであるインターフェイスを第 2 言語のバッファーでプライマリ ファイルの場所にマップするために必要な基本的なサービスを提供します。

     たとえば、1 つの *.aspx* ASP、HTML、およびすべてのコードに含まれているファイル、プライマリ ファイルが含まれます。 ただし、セカンダリ バッファーには、有効なコード ファイル、2 次バッファーを作成する、クラス定義と共に含まれているコードのみが含まれています。 バッファー コーディネーターは、その他の 1 つのバッファーに編集の調整作業を処理します。

4.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>第一言語には、メソッドはバッファー コーディネーター、バッファー内でどのようなテキストがセカンダリ バッファー内の対応するテキストにマップされます。

     配列で、言語に合格、<xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping>構造体は、現在プライマリとセカンダリのスパンのみ含みます。

5.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A>メソッドと<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A>メソッドは、プライマリとセカンダリ バッファーからマッピングを提供します。