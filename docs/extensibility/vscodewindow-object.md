---
title: "VSCodeWindow オブジェクト |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2de0998a3d89c1af3e18fa60aa3f8511716f6165
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="vscodewindow-object"></a>VSCodeWindow オブジェクト
コード ウィンドウは通常 1 つまたは複数のテキスト ビューを含めることができる特殊なドキュメント ウィンドウ、<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>オブジェクト。  
  
 アーキテクチャ上、コード ウィンドウはウィンドウ フレーム内にあるドキュメント ウィンドウです。 機能的には、コード ウィンドウは、他の機能のドキュメント ウィンドウです。 マルチ ドキュメント インターフェイス (MDI) モードでは、コード ウィンドウは、MDI 子フレームです。 詳細については、次を参照してください。[レガシ API を使用してコード ウィンドウをカスタマイズする](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)です。  
  
 次の表にはで示されるインターフェイスが含まれています、<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>オブジェクト。  
  
|メソッド|説明|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|グローバル一意識別子 (GUID) を識別するサービスを検索する汎用アクセス メカニズムを提供します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|1 つまたは複数のコード ビューを含む複数ドキュメント インターフェイス (MDI) 子を表します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|ウィンドウ フレームを設定します。|  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [図形の編集](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)