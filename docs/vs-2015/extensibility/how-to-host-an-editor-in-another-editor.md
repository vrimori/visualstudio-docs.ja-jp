---
title: '方法: 別のエディターで、エディターのホスト |Microsoft Docs'
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
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7bdab7eb1949cb2d1113247c1c537c1a43ccf97
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49208521"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>方法: 別のエディターで、エディターのホスト
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio では、親ウィンドウとしてホスト ウィンドウを指定することで、別の 1 つのエディターをホストできます。 これを行うには、パラメーターを設定<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>と<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>子ウィンドウ フレームにします。  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>エディターをホストするウィンドウ フレームを設定するには  
  
1.  ホスト型のエディターとして子ウィンドウを作成してエディターを指定します。  
  
     このウィンドウは、エディターのテキストが変わります。  
  
2.  使用してホスト側エディターを作成、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>または<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>メソッド。  
  
3.  設定、<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>と<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>プロパティをパラメーターとしてこれらのプロパティを渡すことによってホストされているエディターのウィンドウ フレームの実装で、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>メソッドでは、それぞれします。  
  
     これらのパラメーターを取得する必要がある場合は、これらのプロパティを渡す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>メソッド。  
  
4.  呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>メソッドが含まれているエディター。  
  
     ホストされているコンテナー エディターのウィンドウで、エディターが表示されます。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 **アプリケーション デザイナー** Visual Studio Team Edition for Architects で別のエディターをホストしているエディター ウィンドウ フレームの例に示します。 **アプリケーション デザイナー**その右側のウィンドウの他のデザイナーをホストします。 デザイナー パネル (または**プロパティ**ページ) のウィンドウ フレームに含まれているデザイナーの各追加されます。

