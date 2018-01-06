---
title: "ドロップダウン バー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7058c0b93cd0ff4afb2a13b625cd7ef034b03699
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="drop-down-bar"></a>ドロップダウン バー
ドロップダウン バーは、コード ウィンドウの上部に提供され、2 つのドロップダウン リストが含まれています。  
  
## <a name="drop-down-bar-interfaces"></a>ドロップダウン バー インターフェイス  
 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]、たとえば、ドロップダウン バーには、リストが含まれます。[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]アイテムと[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]アイテム メンバー関数は、次の図に示すようにします。  
  
 ![ドロップ &#45; バーを下](../extensibility/media/vsdropdown_bar.gif "vsDropdown_bar")  
ドロップダウン バー  
  
 ドロップダウン バーを実装する場合は、プライマリの重要度の 4 つのインターフェイスがあります。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     ドロップダウン バーのコンテンツを挿入するには、このインターフェイスを実装します。 各ドロップダウンの組み合わせは、テキスト形式またはテキストを含めることができます (太字、下線、または [斜体])、ウィンドウのテキストのフォントの色指定または色分け、グレーのフォントを持つことができ、必要に応じてドロップダウン項目の横にある小さいビットマップを指定できます。 ような<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>インターフェイス、ビットマップ イメージがイメージ リストで提供されます。 ドロップダウンの組み合わせごとに、別のイメージ リストを持つことができます。ただし、各イメージ リストは、同じ高さのイメージを含める必要があります。 さらを使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A>メソッドの組み合わせごとに、ツールヒントを指定することができます。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     作成するか、コード ウィンドウのドロップダウン バーを破棄するには、このインターフェイスを呼び出します。 このインターフェイスは、呼び出すことによって、コード ウィンドウにドロップダウン バーを既に接続かどうかを確認にも使用できます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A>メソッドです。 呼び出す<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>の<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>から<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>です。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     ドロップダウン バーと直接通信するには、このインターフェイスを呼び出します。 このインターフェイスを使用するには、ドロップダウン リストの更新を強制バーの内容またはリスト ボックスのいずれかで選択を変更します。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     登録されている場合、`ShowDropdownBarOption`言語サービスのレジストリ キーにし、コード ウィンドウ マネージャー監視する必要がありますドロップダウン バーを表示するかどうかに関するユーザー設定と同期するには、このイベント。 言語サービス キーでは、このオプションを登録しないかどうかで、ドロップダウン バーを非表示オプションが無効になっている、**オプション**メニュー。  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>コード ウィンドウにドロップダウン バーをアタッチします。  
 ドロップダウン リストに言語サービスをアタッチするドロップダウン バーが作成されると、コード ウィンドウに関連付けると、バーの場合、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>メソッドが呼び出されます。 呼び出し、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A>メソッドは、ドロップダウン バーの存在しない場合、呼び出しが存在しないことを示します。<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>です。 アクセスする、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>インターフェイスでは、呼び出す<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>から、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>ポインターにする場合に返されます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>実装がアタッチされています。  
  
## <a name="see-also"></a>参照  
 [レガシ API を使用してコード ウィンドウをカスタマイズします。](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [従来の言語サービスでのナビゲーション バーのサポート](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)