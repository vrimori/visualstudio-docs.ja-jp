---
title: "方法: 検索の実装とメカニズムを置換 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c971d4565c95cab23e683a1a4f20c75ebea81b8f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>方法: 検索の実装とメカニズムを置換
Visual Studio には、検索と置換を実装する 2 つの方法が用意されています。 1 つの方法では、テキスト、イメージをシェルに渡すし、検索、強調表示、および置換テキストを処理できます。 これにより、ユーザーが複数のテキスト範囲を指定できます。 また、VSPackage では、この機能自体を制御できます。 どちらの場合も、現在のターゲットとすべての開いているドキュメントのターゲットについて、シェルに通知する必要があります。  
  
### <a name="to-implement-findreplace"></a>検索と置換を実装するには  
  
1.  実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>フレームのプロパティによって返されるオブジェクトの 1 つのインターフェイス<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>または<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>です。 カスタム エディターを作成する場合は、カスタム エディターのクラスの一部としてこのインターフェイスを実装する必要があります。  
  
2.  使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A>メソッドとテキストの画像の検索を実装するかどうかを示すために、エディターをサポートするオプションを指定します。  
  
     エディターでは、テキストの画像の検索をサポートする場合は、実装<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>です。  
  
     それ以外の場合、実装<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>です。  
  
3.  実装する場合、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>メソッドを呼び出すことによって、検索タスクを簡略化できます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>インターフェイスです。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>