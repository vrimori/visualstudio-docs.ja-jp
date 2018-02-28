---
title: "方法: 別のエディターでエディターをホスト |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 685ad1d619fdf9f04fe1a9cd1122a9e6ed3ba025
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-an-editor-in-another-editor"></a>方法: 別のエディターでエディターをホストします。
Visual Studio では、親ウィンドウとして、ホスト ウィンドウを指定することによって、別の 1 つのエディターをホストできます。 パラメーターを設定するには、<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>と<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>子ウィンドウ フレームにします。  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>エディターをホストするウィンドウ フレームを設定するには  
  
1.  子ウィンドウを作成することで、ホスト型のエディターとしてエディターを指定します。  
  
     このウィンドウは、エディターのテキストが移動されます。  
  
2.  使用してホスト側エディターを作成、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>または<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>メソッドです。  
  
3.  設定、<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>と<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>プロパティへのパラメーターとしてこれらのプロパティを渡すことによってホストされているエディターのウィンドウ フレームの実装で、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>メソッド、それぞれします。  
  
     これらのパラメーターを取得する必要がある場合は、これらのプロパティを渡す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>メソッドです。  
  
4.  呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>包含エディターのメソッドです。  
  
     エディターは、ホストされているエディターのペインで、コンテナーが表示されます。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 **アプリケーション デザイナー**設計者向けの Visual Studio Team Edition で別のエディターをホストしているエディター ウィンドウ フレームの例を示します。 **アプリケーション デザイナー**右側のウィンドウで、他のデザイナーをホストします。 デザイナーのパネル (または**プロパティ** ページ) を含むウィンドウ フレームに含まれているデザイナーの各が追加されます。