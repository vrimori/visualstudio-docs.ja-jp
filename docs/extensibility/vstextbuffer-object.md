---
title: "VSTextBuffer オブジェクト | Microsoft Docs"
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
  - "VSTextBuffer"
helpviewer_keywords: 
  - "VSTextBuffer オブジェクト、参照"
  - "ビュー [Visual Studio SDK] VSTextBuffer オブジェクト"
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# VSTextBuffer オブジェクト
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

テキスト バッファー オブジェクトでは、一般に、ファイルに関連付けられている Unicode テキストのストリームを表します。 A <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> ウィザード場合に、コア エディターのコンテキストの外部オブジェクトを使用できます。  
  
 次の表は、インターフェイスを示しています。 `VSTextBuffer`します。  
  
|メソッド|説明|  
|----------|--------|  
|[IOleCommandTarget](http://msdn.microsoft.com/library/windows/desktop/ms683797)|標準の OLE インターフェイスです。 主に、元に戻す\/やり直しのバッファーの処理に使用します。|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|標準の OLE インターフェイスです。|  
|[IPersistStream](http://msdn.microsoft.com/library/windows/desktop/ms690091)|標準の OLE インターフェイスです。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|複合語のアクション \(つまり、元に戻す\/やり直しの 1 つの単位にグループ化されているアクション\) を作成できます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|テキスト バッファーによって管理されるドキュメント データの永続化を有効にします。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|基本的なサービスを提供します。多くのクライアントによって使用されます。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|バッファーを検索するために使用します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|読み取りし、書き込みの 2 次元座標を使用して機能します。`IVsTextBuffer` から継承します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|読み取りし、書き込みの 1 次元の座標を使用して機能します。`IVsTextBuffer` から継承します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|高速でストリーム指向シーケンシャルへのアクセス、バッファー内のテキストを提供します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|プロパティのジェネリック コレクションへのアクセスを提供します。 最も重要なプロパティは、名前、またはバッファーのモニカーです。 このインターフェイスでバッファーの独自のランダムなデータを格納するには、GUID を作成して、キーとして使用します。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|イベントのコネクション ポイントをサポートします。|  
  
## 解説  
 `VSTextBuffer` で見つかることが、 `QueryInterface` で呼び出す `IVsTextBuffer`します。 詳細については、次を参照してください。 [テキスト バッファー](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)します。  
  
## 参照  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Figures Edit](http://msdn.microsoft.com/ja-jp/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)