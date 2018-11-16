---
title: 言語に含まれている |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4ff50fe0fe156c548351c378ba3a256e230ec43
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772026"
---
# <a name="contained-languages"></a>含まれている言語
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)] 

  
*言語に含まれている*は他の言語に含まれている言語。 たとえば、HTML で[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]ページに含めることができます[!INCLUDE[csprcs](../includes/csprcs-md.md)]または[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]スクリプト。 デュアル言語アーキテクチャは、.aspx ファイルのエディター、HTML とスクリプト言語の両方の IntelliSense、色付け、およびその他の編集機能を提供する必要があります。  
  
## <a name="implementation"></a>実装  
 含まれている言語を実装する必要がある最も重要なインターフェイスは、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>インターフェイス。 このインターフェイスは、主言語内でホストされる任意の言語によって実装されます。 言語サービスの colorizer、テキスト ビューのフィルター、およびプライマリ言語サービスの ID にアクセスします。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>を作成することができます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>インターフェイス。 次の手順では、含まれている言語を実装する方法を示します。  
  
1.  使用`QueryService()`言語サービスの ID とのインターフェイス ID を取得する、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>します。  
  
2.  呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A>を作成する方法、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>インターフェイス。 渡す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>インターフェイス、1 つまたは複数[項目の Id](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>)と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>インターフェイス。  
  
3.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>テキスト バッファーのコーディネーター オブジェクトであるインターフェイスを第 2 言語のバッファーでプライマリ ファイルの場所にマップするために必要な基本的なサービスを提供します。  
  
     たとえば、1 つの .aspx ファイルでプライマリ ファイルが含まれています、ASP、HTML に含まれるすべてのコード。 ただし、セカンダリのバッファーには、有効なコード ファイル、2 次バッファーを作成する、クラス定義と共に、含まれているコードのみが含まれています。 バッファー コーディネーターは、その他の 1 つのバッファーに編集の調整作業を処理します。  
  
4.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>第一言語には、メソッドはバッファー コーディネーター、バッファー内でどのようなテキストがセカンダリ バッファー内の対応するテキストにマップされます。  
  
     配列で、言語に合格、<xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping>構造体は、現在プライマリとセカンダリのスパンのみ含みます。  
  
5.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A>メソッドと<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A>メソッドは、プライマリとセカンダリ バッファーからマッピングを提供します。

