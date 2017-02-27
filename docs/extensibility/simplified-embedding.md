---
title: "簡略化された埋め込み | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "埋め込みエディター [Visual Studio SDK] カスタム - 単純な表示します。"
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# 簡略化された埋め込み
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

単純埋め込むとエディターでドキュメントのビュー オブジェクトは浮き出た \(つまり子に実装されます\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] または <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> のインターフェイスはウィンドウでコマンドを処理すると有効になります。  簡体字エディターを埋め込むとアクティブなコントロールをホストできません。  単純埋め込みのエディターを作成するために使用されるオブジェクトを次の図に示します。  
  
 ![簡略化された埋め込みエディター グラフィック](../extensibility/media/vssimplifiedembeddingeditor.png "vsSimplifiedEmbeddingEditor")  
単純埋め込みのエディター  
  
> [!NOTE]
>  この図のオブジェクトの`CYourEditorFactory` のオブジェクトだけ標準ファイル ベースのエディターを作成する必要があります。  カスタム エディターを作成するとエディターに独自のプライベート永続化機能があるため <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> を実行する必要はありません。  ただしカスタムのエディターで実行する必要があります。  
  
 単純埋め込みのエディターを作成するために実行されたすべてのインターフェイスは `CYourEditorDocument` のオブジェクトに含まれています。  ただしドキュメント データのビューをサポートするように次の表に示すように独立したデータにインターフェイスとビュー オブジェクトを分割します。  
  
|Interface|インターフェイスの場所|\[条件\]|  
|---------------|-----------------|------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|ビュー|親ウィンドウへの接続を指定します。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|ビュー|コマンドのハンドル。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|ビュー|有効なステータス バーを更新します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|ビュー|**ツールボックス**  の項目を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Data|ファイルの変更時に通知を送信します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Data|ファイルの種類の名前を付けて保存機能を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Data|ドキュメントの永続性を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Data|トリガーの読み込みなどのファイルの変更イベントの抑制を許可します。|