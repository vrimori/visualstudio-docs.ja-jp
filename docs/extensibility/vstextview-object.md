---
title: "VSTextView オブジェクト |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f169c3302b3e6fd72e5017193e34836ed3e5340e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="vstextview-object"></a>VSTextView オブジェクト
テキスト ビューは、ユーザーを表示およびテキスト バッファーの Unicode テキストを編集できるウィンドウです。 基本的には、ビューは、ほとんどのユーザーではこれをエディターとして参照します。 ビューは、バッファーからさまざまなテキスト レイヤー (ワード ラップ、アウトライン表示テキスト、およびなど) で区切られた、ため、ビューは、バッファー内のテキストの正確な表現である保証されません。 テキスト ビューの詳細については、次を参照してください[レガシ API を使用してテキスト ビューにアクセスする。](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 次の表で示されるインターフェイスを示しています、<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>オブジェクト。  
  
|Interface|説明|  
|---------------|-----------------|  
|[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)|標準の OLE インターフェイスです。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|標準の OLE インターフェイスです。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|標準の OLE インターフェイスです。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|標準の OLE インターフェイスです。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|複合アクション (つまり、元に戻す/やり直しの 1 つの単位にグループ化されているアクション) を作成できます。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|管理およびビューにアクセスするためには、基本的なメソッドを提供します。 `IVsTextView`スレッド セーフであります。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|作成し、ウィンドウ ペインを管理します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|テキストのレイヤーと通信します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|別のスレッドから、ビューでの操作を実行します。|  
  
## <a name="see-also"></a>参照  
 [図形の編集](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [VSTextBuffer オブジェクト](../extensibility/vstextbuffer-object.md)   
 [レガシ API を使用してテキスト ビューにアクセスします。](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)