---
title: プロパティ ウィンドウの選択の追跡の発表 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], property pages support
- property pages, tracking selection
- Properties window, tracking selection
- selection, tracking
- editors [Visual Studio SDK], Properties window support
ms.assetid: a7536f82-afd7-4894-9a60-84307fb92b7e
caps.latest.revision: 13
manager: douge
ms.openlocfilehash: 9639e0347689fc99e0b43c4b69394b522af984da
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246741"
---
# <a name="announcing-property-window-selection-tracking"></a>プロパティ ウィンドウの選択の追跡の発表
使用する場合、**プロパティ**ウィンドウまたは**プロパティ**フォーム、テキスト、またはするプロパティを表示する方法の完全な知識が必要し、選択などページします。選択範囲を調整します。 たとえば、選択範囲の 1 つまたは複数の選択肢があるかどうかを認識する必要があります。 選択範囲の種類 (1 つまたは複数) を使用して、IDE を発表する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>インターフェイス。 このインターフェイスで必要な情報を提供する、**プロパティ**ウィンドウ。  
  
### <a name="to-announce-selection-to-the-environment"></a>選択範囲を環境のことをお知らせ  
  
1.  呼び出す`QueryInterface`の<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>します。  
  
    1.  これを行うには、作成時に、ビューに渡されたサイト ポインターを使用します。  
  
    2.  呼び出す`QueryService`のビューから、`SID_STrackSelection`サービス。  
  
         ポインターが返されます<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>します。  
  
2.  呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>選択内容が変更されるたびにメソッドを実装するオブジェクトへのポインターを渡す<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>します。  
  
     選択コンテナー オブジェクトの 1 つまたは複数選択のいずれかを使用することができでは、選択した情報が含まれています、`IDispatch`オブジェクト。 呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>メソッドは、通知、**プロパティ**選択が変更されたウィンドウ。 **プロパティ**ウィンドウにあるオブジェクトが使用し、<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>を 1 つまたは複数選択が発生したかどうかを実際のオブジェクトの選択項目を決定します。  
  
     複数の選択を指定する場合、**プロパティ**ウィンドウ オブジェクトの共通プロパティの交差部分を検索します。 1 つのオブジェクトの選択では、指定した場合、**プロパティ**ウィンドウでは、すべての 1 つのオブジェクトのプロパティが表示されます。  
  
## <a name="see-also"></a>関連項目  
 [プロパティの拡張](../extensibility/internals/extending-properties.md)   
 [プロパティ ページ](../extensibility/internals/property-pages.md)