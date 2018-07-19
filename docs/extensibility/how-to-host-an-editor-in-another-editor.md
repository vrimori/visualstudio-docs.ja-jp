---
title: '方法: 別のエディターで、エディターのホスト |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 53b4f02135b18c4641d4e802df3d1124a5d06b47
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058387"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>方法: 別のエディターで、エディターのホスト

Visual Studio では、親ウィンドウとしてホスト ウィンドウを指定することで別の 1 つのエディターをホストできます。 これを行うには、パラメーターを設定<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentHwnd>と<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentFrame>子ウィンドウ フレームにします。

## <a name="to-set-up-the-window-frame-to-host-an-editor"></a>エディターをホストするウィンドウ フレームを設定するには

1.  ホスト型のエディターとして子ウィンドウを作成してエディターを指定します。

     このウィンドウは、エディターのテキストが変わります。

2.  使用してホスト側エディターを作成、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>または<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>メソッド。

3.  設定、<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentHwnd>と<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentFrame>プロパティをパラメーターとしてこれらのプロパティを渡すことによってホストされているエディターのウィンドウ フレームの実装で、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>メソッドでは、それぞれします。

     これらのパラメーターを取得する必要がある場合は、これらのプロパティを渡す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>メソッド。

4.  呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>メソッドが含まれているエディター。

     ホストされているコンテナー エディターのウィンドウで、エディターが表示されます。

## <a name="robust-programming"></a>信頼性の高いプログラミング

**アプリケーション デザイナー** Visual Studio Team Edition for Architects で別のエディターをホストしているエディター ウィンドウ フレームの例に示します。 **アプリケーション デザイナー**その右側のウィンドウの他のデザイナーをホストします。 デザイナー パネル (または**プロパティ**ページ) のウィンドウ フレームに含まれているデザイナーの各追加されます。