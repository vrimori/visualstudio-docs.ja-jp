---
title: "VSCodeWindow オブジェクト | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSCodeWindow"
helpviewer_keywords: 
  - "ビュー [Visual Studio SDK] VSCodeWindow オブジェクト"
  - "VsCodeWindow オブジェクト"
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# VSCodeWindow オブジェクト
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

コード ウィンドウは、通常 1 つ以上のテキスト ビューを含めることができる特殊なドキュメント ウィンドウ、 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> オブジェクトです。  
  
 アーキテクチャとしては、コード ウィンドウにはウィンドウ フレーム内にあるドキュメント ウィンドウです。 機能的には、コード ウィンドウには、他の機能のドキュメント ウィンドウができます。 マルチ ドキュメント インターフェイス \(MDI\) モードでは、コード ウィンドウは、MDI 子フレームです。 詳細については、「[レガシ API を使用してコード ウィンドウをカスタマイズします。](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)」を参照してください。  
  
 次の表に、インターフェイス、 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> オブジェクトです。  
  
|メソッド|説明|  
|----------|--------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|グローバル一意識別子 \(GUID\) を識別するサービスを検索する汎用アクセス メカニズムを提供します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|1 つまたは複数のコード ビューを含む複数ドキュメント インターフェイス \(MDI\) 子を表します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|ウィンドウ フレームを格納します。|  
  
## 参照  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Figures Edit](http://msdn.microsoft.com/ja-jp/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)