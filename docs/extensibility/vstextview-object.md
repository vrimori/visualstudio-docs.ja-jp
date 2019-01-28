---
title: VSTextView オブジェクト |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f8de4ad6c467c2f72743bd6e5aa3a80f629c6f1b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953892"
---
# <a name="vstextview-object"></a>VSTextView オブジェクト
テキスト ビューは、ユーザーの表示し、テキスト バッファーの Unicode テキストを編集できるウィンドウです。 基本的には、ビューは、ほとんどのユーザーではこれをエディターとして参照します。 ビューは、バッファーからさまざまなテキスト レイヤー (ワード ラップ、アウトラインのテキスト) で区切られた、ため、ビューは、バッファー内のテキストの正確な表現には保証されません。 テキスト ビューの詳細については、次を参照してください[レガシ API を使用してテキスト ビューにアクセスする。](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 次の表は、インターフェイス、<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>オブジェクト。  
  
|Interface|説明|  
|---------------|-----------------|  
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|標準の OLE インターフェイス。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|標準の OLE インターフェイス。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|標準の OLE インターフェイス。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|標準の OLE インターフェイス。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|複合アクション (元に戻す/やり直しの 1 つの単位にグループ化アクション) を作成できます。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|管理すると、ビューにアクセスするには、基本的なメソッドを提供します。 `IVsTextView` 安全なスレッドがありません。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|作成し、ウィンドウ ペインを管理します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|テキスト レイヤーとやり取りします。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|別のスレッドから、ビューに対する操作を実行します。|  
  
## <a name="see-also"></a>関連項目  
 [図の編集](https://www.microsoft.com/download/details.aspx?id=55984)   
 [VSTextBuffer オブジェクト](../extensibility/vstextbuffer-object.md)   
 [従来の API を使用してへのアクセスのテキスト ビュー](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)