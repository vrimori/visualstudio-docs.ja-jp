---
title: 子プロパティを持つプロパティを非表示 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- properties [Visual Studio SDK], hiding
- Properties window, hiding properties that have child properties
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
manager: douge
ms.openlocfilehash: bd340b748311bbb257ed0c4bbfe7b972cbf7beb9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545479"
---
# <a name="hiding-properties-that-have-child-properties"></a>子プロパティを持つ非表示のプロパティ
子プロパティを持つプロパティを非表示にします。  
  
-   プロジェクトが入れ子になっている場合は、親がプログラムによってプロジェクト、子プロジェクトの一部の側面を制御します。  
  
-   場合は、コントロールの特殊なデザイナーを使用して、コントロールのすべてのプロパティにフル アクセスを開発者に提供したくないです。  
  
-   場合は、オブジェクトのスコープの所有権を持っているし、プロパティの表示を制限します。  
  
### <a name="to-hide-properties-that-have-child-properties"></a>子プロパティを持つプロパティを非表示にするには  
  
1.  設定、`pfDisplay`パラメーター<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A>に`FALSE`します。  
  
2.  設定、`pfHide`パラメーター<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A>に`TRUE`します。  
  
## <a name="see-also"></a>関連項目  
 [プロパティ表示グリッド](../extensibility/internals/properties-display-grid.md)