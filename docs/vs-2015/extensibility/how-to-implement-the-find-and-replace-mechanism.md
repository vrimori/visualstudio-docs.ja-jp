---
title: '方法: 検索の実装とメカニズムを置換 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eaae77979fc15954b4480a038c791a15bd95ab65
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535345"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>方法: 検索の実装とメカニズムを置換
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: 検索と置換のメカニズムを実装](https://docs.microsoft.com/visualstudio/extensibility/how-to-implement-the-find-and-replace-mechanism)します。  
  
Visual Studio には、検索/置換を実装する 2 つの方法が用意されています。 1 つの方法が、テキスト、イメージをシェルに渡すし、検索、強調表示、および置換テキストを処理できます。 これにより、複数のテキスト範囲を指定できます。 または、VSPackage では、この機能自体を制御できます。 どちらの場合も、現在のターゲットとすべての開いているドキュメントのターゲットについて、シェルに通知する必要があります。  
  
### <a name="to-implement-findreplace"></a>検索/置換を実装するには  
  
1.  実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>フレーム プロパティによって返されるオブジェクトのいずれかのインターフェイス<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>または<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>します。 カスタム エディターを作成する場合は、カスタム エディターのクラスの一部としてこのインターフェイスを実装する必要があります。  
  
2.  使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A>メソッドのエディターをサポートするオプションを指定して、テキスト イメージの検索を実装するかどうかを示します。  
  
     エディターでは、テキスト イメージの検索をサポートする場合は、実装<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>します。  
  
     それ以外の場合、実装<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>します。  
  
3.  実装する場合、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>メソッドを呼び出すことによって検索タスクを簡略化できます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>インターフェイス。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>

