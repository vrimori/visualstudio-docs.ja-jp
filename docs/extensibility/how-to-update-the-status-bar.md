---
title: "方法: ステータス バーの更新 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 76801810aafa3bd4048776ca38385ad1cf508d94
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-update-the-status-bar"></a>方法: ステータス バーの更新
**ステータス バー**ステータス テキスト行またはインジケーターの 1 つ以上含まれている多くのアプリケーション ウィンドウの下部にあるコントロール バーがあります。  
  
### <a name="to-update-the-status-bar"></a>ステータス バーを更新するには  
  
1.  実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>フォーム ビューとコード ビューなどのエディターが提供する各個々 のビュー オブジェクト (DocView) にします。  
  
2.  IDE を呼び出すと<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>の情報を更新、**ステータス バー**のメソッドを呼び出すことによって<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>です。  
  
    > [!NOTE]
    >  IDE 呼び出し<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>のみ、ドキュメント ウィンドウが最初に有効な場合です。 ドキュメント ウィンドウがアクティブになっている時間の残りの部分を更新する必要があります、**ステータス バー**エディター変更の状態と情報。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 A**ステータス バー** 4 つの個別のフィールドが含まれています。  
  
-   状態テキスト  
  
-   進行状況バー  
  
-   アニメーションのアイコン  
  
-   エディターについて  
  
 詳細については、次を参照してください。[ステータス バー](/cpp/mfc/status-bars)です。  
  
 IDE を自動的に呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>のメソッド、<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>ドキュメント ウィンドウがアクティブになったときの実装です。  
  
 VSPackage 実装者は、ステータス バーにステータス テキストを更新します。 状態テキスト フィールドが空のテキストに設定されている場合、IDE が「準備完了」には、この文字列をリセット ("") のアイドル時間にします。  
  
## <a name="see-also"></a>参照  
 [ステータス バー](/cpp/mfc/status-bars)