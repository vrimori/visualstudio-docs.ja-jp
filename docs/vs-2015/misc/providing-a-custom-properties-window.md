---
title: カスタム プロパティ ウィンドウの提供 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- property browsers, providing
- Properties window, providing your own
ms.assetid: 408dcdef-8ef9-4644-97d2-f311cd35824f
caps.latest.revision: 12
manager: douge
ms.openlocfilehash: 8b3aeae11e087b6a6bd662ed32564d93062426df
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186278"
---
# <a name="providing-a-custom-properties-window"></a>カスタム プロパティ ウィンドウの提供
独自に提供することは**プロパティ**延長する代わりに、特定のプロジェクト システム ウィンドウ、**プロパティ**ウィンドウによって提供される、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]統合開発環境 (IDE) です。 最もよく発生したシナリオ ウィンドウ フレームに配置されたオブジェクトを実装する自分で場合です。  
  
 さまざまな方法へのアクセスには、ウィンドウ フレーム内に配置するオブジェクトを実装していませんが、他のいくつかの方法でアクセス権が引き続き、イベント、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>インターフェイスのこのページで、前の手順に記載されています。  
  
### <a name="to-provide-your-properties-window"></a>[プロパティ] ウィンドウを提供するには  
  
1.  定義を表す GUID、**プロパティ**ウィンドウの実装。  
  
2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>実装を使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>サービスを提供、**プロパティ**Visual Studio 環境にサービスとしてのウィンドウ。  
  
### <a name="to-call-your-properties-window"></a>[プロパティ] ウィンドウを呼び出す  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> メソッドを呼び出します。  
  
2.  `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>から、<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>に渡される、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A>メソッド。  
  
3.  取得<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>から<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>サービス。  
  
4.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>最初のパラメーターを設定して`SEID_PropertyBrowserSID`(から取得した、<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>列挙型)、3 番目のパラメーターでは、`varValue`を表す GUID の文字列形式を表す、**プロパティ**ウィンドウです。 最初の作成時に 1 回だけ呼び出しを行う、**プロパティ**ドキュメント ウィンドウのウィンドウ。 呼び出しの後にこの**プロパティ**ウィンドウは、ウィンドウ フレームに関連付けられています。  
  
### <a name="to-obtain-the-window-frame-object-when-you-are-not-the-implementer"></a>実装側ではない場合は、ウィンドウ フレーム オブジェクトを取得するには  
  
-   できます`QueryService`の<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>からサービス<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>パラメーターと共に`propid`に設定<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>します。  
  
-   アクティブなドキュメント ウィンドウを取得するには呼び出すことによって<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A>SVsMonitorSelection サービスを使用します。 パラメーターを設定`elementid`に`SEID_WindowFrame`から作成した、<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>列挙体。  
  
## <a name="see-also"></a>関連項目  
 [プロパティの拡張](../extensibility/internals/extending-properties.md)   
 [プロパティ ウィンドウのフィールドとインターフェイス](../extensibility/internals/properties-window-fields-and-interfaces.md)