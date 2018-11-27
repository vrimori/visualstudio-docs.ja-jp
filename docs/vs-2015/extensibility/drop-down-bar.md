---
title: ドロップダウン バー |Microsoft Docs
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
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: da48806d6be6b19dc3681b19e95ac7664656eeb0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791145"
---
# <a name="drop-down-bar"></a>ドロップダウン バー
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ドロップダウン バーは、コード ウィンドウの上部にあるは提供され、2 つのドロップダウン リストが含まれています。  
  
## <a name="drop-down-bar-interfaces"></a>ドロップダウン バー インターフェイス  
 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]、たとえば、ドロップダウン バーには、リストが含まれます。[!INCLUDE[vcprvc](../includes/vcprvc-md.md)]項目と[!INCLUDE[vcprvc](../includes/vcprvc-md.md)]項目メンバー関数は、次の図に示すようにします。  
  
 ![Drop&#45;バーを下](../extensibility/media/vsdropdown-bar.gif "vsDropdown_bar")  
ドロップダウン バー  
  
 ドロップダウン バーを実装する場合は、プライマリの重要度の 4 つのインターフェイスがあります。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     ドロップダウン バーのコンテンツを挿入するには、このインターフェイスを実装します。 ドロップダウン リストの組み合わせは、プレーン テキストまたは手の込んだテキストに含めることができます (太字、下線、または斜体) ウィンドウのテキストのフォント色または色分け、グレーのフォントを持つことができます、および、必要に応じて、ドロップダウン リストの項目の横にある小さいビットマップを指定できます。 ような<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>インターフェイス、イメージ リストで、ビットマップ イメージが提供されます。 ドロップダウン リストの組み合わせごとに、別のイメージ リストを持つことができます。ただし、各イメージの一覧には、同じ高さのイメージを含める必要があります。 さらを使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A>メソッドの組み合わせごとにツールヒントを提供できます。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     このインターフェイスを作成するか、コード ウィンドウのドロップダウン バーの破棄を呼び出します。 このインターフェイスが呼び出すことによって、コード ウィンドウにドロップダウン バーを既にアタッチかどうかを判断することもでき、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A>メソッド。 呼び出す<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>の<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>から<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>します。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     ドロップダウン バーと直接通信するには、このインターフェイスを呼び出します。 このインターフェイスを使用するには、ドロップダウン リストの更新を強制するコンテンツ バーまたはリスト ボックスのいずれかで選択を変更します。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     登録している場合、`ShowDropdownBarOption`言語サービスのレジストリ キーにし、コード ウィンドウ マネージャー監視する必要がありますドロップダウン バーを表示するかどうかに関するユーザー設定と同期するには、このイベント。 ドロップダウン バーを非表示オプションが無効になっている場合、言語サービス キーでこのオプションを登録しないでください、**オプション**メニュー。  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>コード ウィンドウにドロップダウン バーのアタッチ  
 作成時に、コード ウィンドウにドロップダウン バーを接続するに言語サービスは、ドロップダウン リストにアタッチする必要がありますバーの場合に、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>メソッドが呼び出されます。 呼び出し、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A>メソッドは、ドロップダウン バーの存在しない場合、呼び出しが存在しないことを示します。<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>します。 アクセスする、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>インターフェイスを呼び出す<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>から、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>返されるポインターにするときに、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>実装がアタッチされました。  
  
## <a name="see-also"></a>関連項目  
 [レガシ API を使用してコードの Windows をカスタマイズします。](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [従来の言語サービスでのナビゲーション バーのサポート](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

