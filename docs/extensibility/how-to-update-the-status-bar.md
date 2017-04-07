---
title: "方法: ステータス バーの更新 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 15b207618487fd49516849c591ef80c56b618ce0
ms.lasthandoff: 04/05/2017

---
# <a name="how-to-update-the-status-bar"></a>方法: ステータス バーの更新
**ステータス バー**ステータス テキスト行またはインジケーターの 1 つまたは複数を含む多くのアプリケーション ウィンドウの下部にあるコントロール バーがあります。  
  
### <a name="to-update-the-status-bar"></a>ステータス バーを更新するには  
  
1.  実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>、フォーム ビューとコード ビューなどのエディターが提供する各個々 のビュー オブジェクト (DocView).</xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>  
  
2.  IDE を呼び出すと<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>の情報を更新、**ステータス バー** <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>のメソッドを呼び出すことによって</xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>  
  
    > [!NOTE]
    >  IDE 呼び出し<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>のみ、ドキュメント ウィンドウが最初に有効な場合</xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>。 ドキュメント ウィンドウがアクティブになっている時間の残りの部分を更新する必要があります、**ステータス バー**エディター変更の状態と情報。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 A**ステータス バー** 4 つの個別のフィールドが含まれています。  
  
-   状態テキスト  
  
-   進行状況バー  
  
-   アニメーションのアイコン  
  
-   エディターについて  
  
 詳細については、次を参照してください。[ステータス バー](/cpp/mfc/status-bars)です。  
  
 IDE を自動的に呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>のメソッド、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>、ドキュメント ウィンドウがアクティブになったときの実装</xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser></xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>。  
  
 VSPackage 実装者は、ステータス バーにステータス テキストを更新します。 状態テキスト フィールドが空のテキストに設定されている場合、IDE が「準備完了」には、この文字列をリセット ("") のアイドル時間にします。  
  
## <a name="see-also"></a>関連項目  
 [ステータス バー](/cpp/mfc/status-bars)
