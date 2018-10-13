---
title: '方法: ステータス バーの更新 |Microsoft Docs'
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
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cd784b718fb370ec8ce04937119a9d64995cdd8d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49301094"
---
# <a name="how-to-update-the-status-bar"></a>方法: ステータス バーの更新
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**ステータス バー**状態テキストの行または評価指標の 1 つまたは複数を含む多くのアプリケーション ウィンドウの下部にあるコントロール バーがあります。  
  
### <a name="to-update-the-status-bar"></a>ステータス バーを更新するには  
  
1.  実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>フォーム ビューとコード ビューなど、エディターを提供する各個々 のビュー オブジェクト (DocView)。  
  
2.  IDE を呼び出すと<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>の情報を更新、**ステータス バー**のメソッドを呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>します。  
  
    > [!NOTE]
    >  IDE 呼び出し<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>のみ、ドキュメント ウィンドウが最初に有効な場合。 ドキュメント ウィンドウがアクティブになっている時間の残りの部分を更新する必要があります、**ステータス バー**エディターの変更の状態と情報。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 A**ステータス バー** 4 つの個別のフィールドが含まれています。  
  
-   状態テキスト  
  
-   進行状況バー  
  
-   アニメーション化されたアイコン  
  
-   エディターについて  
  
 詳細については、次を参照してください。[ステータス バー](http://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)します。  
  
 IDE を自動的に呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>のメソッド、<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>実装、ドキュメント ウィンドウがアクティブになります。  
  
 VSPackage の実装者は、ステータス バーで、ステータス テキストを更新します。 状態のテキスト フィールドが空のテキストに設定されている場合、IDE が「準備完了」には、この文字列をリセットします ("") のアイドル時間にします。  
  
## <a name="see-also"></a>関連項目  
 [ステータス バー](http://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)

