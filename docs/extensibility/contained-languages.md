---
title: "言語が含まれている |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c8adf63eed436b5724fcdb32d86ffc7bfb2c1a40
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="contained-languages"></a>格納されている言語
*言語が含まれている*に含まれるその他の言語の言語です。 たとえば、HTML で[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]ページを含めることがあります[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]または[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]スクリプト。 デュアル言語アーキテクチャは、.aspx ファイル エディターの IntelliSense、色付け、およびその他の編集機能を HTML およびスクリプト言語の両方を提供する必要があります。  
  
## <a name="implementation"></a>実装  
 格納されている言語を実装する必要が最も重要なインターフェイスは、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>インターフェイスです。 このインターフェイスは、主言語内でホストできる任意の言語によって実装されます。 これにより、言語サービスの colorizer、テキストの表示フィルター、および主言語サービス ID にアクセス <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>を作成することができます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>インターフェイスです。 次の手順では、格納されている言語を実装する方法を示します。  
  
1.  使用して`QueryService()`言語サービス ID とのインターフェイス ID を取得する、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>です。  
  
2.  呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A>メソッドを作成、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>インターフェイスです。 渡す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>インターフェイス、項目 ID (1 つ以上の<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>、 <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>、または<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>) および<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>インターフェイスです。  
  
3.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>テキスト バッファー コーディネーター オブジェクトであるインターフェイスには、第 2 言語のバッファーにプライマリ ファイルの場所にマップするために必要な基本的なサービスが用意されています。  
  
     たとえば、1 つの .aspx ファイルでは、プライマリ ファイルが含まれています、ASP、HTML およびに含まれているすべてのコード。 ただし、セカンダリのバッファーには、有効なコード ファイル、2 次バッファーを作成する、クラス定義と共に、含まれているコードのみが含まれています。 バッファー コーディネーターは、その他の 1 つのバッファーに編集を調整の作業を処理します。  
  
4.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>第一言語には、メソッドは、そのバッファー内にあるテキストは、2 次バッファー内の対応するテキストにマップされてをバッファー コーディネーターに指示します。  
  
     言語の配列を渡します、<xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping>構造体は、現在のみが含まれています、プライマリとセカンダリのスパン。  
  
5.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A>メソッドおよび<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A>メソッドは、2 次バッファーをその逆のプライマリからのマッピングを指定します。