---
title: '方法: 検索の実装とメカニズムを置換 |Microsoft Docs'
ms.date: 11/04/2016
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fbd41f8f1a86a0b6177b4a1d1498075d6de77030
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636253"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>方法: 検索の実装し、メカニズムを置換

Visual Studio には、検索/置換を実装する 2 つの方法が用意されています。 1 つの方法が、テキスト、イメージをシェルに渡すし、検索、強調表示、および置換テキストを処理できます。 これにより、複数のテキスト範囲を指定できます。 または、VSPackage では、この機能自体を制御できます。 どちらの場合も、現在のターゲットとすべての開いているドキュメントのターゲットについて、シェルに通知する必要があります。

## <a name="to-implement-findreplace"></a>検索/置換を実装するには

1. 実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>フレーム プロパティによって返されるオブジェクトのいずれかのインターフェイス<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>または<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>します。 カスタム エディターを作成する場合は、カスタム エディターのクラスの一部としてこのインターフェイスを実装する必要があります。

2. 使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A>メソッドのエディターをサポートするオプションを指定して、テキスト イメージの検索を実装するかどうかを示します。

   エディターでは、テキスト イメージの検索をサポートする場合は、実装<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>します。

   それ以外の場合、実装<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>します。

3. 実装する場合、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>メソッドを呼び出すことによって検索タスクを簡略化できます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>インターフェイス。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>