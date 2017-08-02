---
title: "埋め込み先編集の有効化 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK], カスタム - 埋め込みのビューのアクティブ化"
ms.assetid: 7d316945-06e0-4d8e-ba3a-0ef96fc75399
caps.latest.revision: 26
caps.handback.revision: 26
manager: "douge"
---
# 埋め込み先編集の有効化
エディター ビューが ActiveX などのアクティブ コントロールをホストしている場合は、インプレース アクティブ化モデルを使用して ActiveX コントロールまたはアクティブ ドキュメント データ オブジェクトとしてエディター ビューを実装する必要があります。  
  
## メニュー、ツール バー、およびコマンドのサポート  
 Visual Studio では、エディター ビューで IDE のメニューおよびツール バーを使用できます。 これらの拡張機能を *OLE インプレース コンポーネント* と呼びます。 詳細については、「<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>」および「<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>」を参照してください。  
  
 ActiveX コントロールを実装すると、他の埋め込みオブジェクトをホストできます。 ドキュメント データ オブジェクトを実装すると、ActiveX コントロールを使用する機能がウィンドウ枠によって制約されます。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> と <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView> の各インターフェイスでは、データとビューを分離できます。 ただし、Visual Studio ではこの機能がサポートされておらず、これらのインターフェイスは、ドキュメント ビュー オブジェクトを表現するためにのみ使用されます。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> サービスを使用するエディターでは、<xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> サービスによって実装される <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> インターフェイスのメソッドを呼び出すことで、メニューとツール バーとコマンドを統合できます。 エディターでは、選択の追跡や元に戻す操作の管理など、Visual Studio の他の機能も提供できます。 詳細については、「[カスタム エディターとデザイナーを作成します。](../extensibility/creating-custom-editors-and-designers.md)」を参照してください。  
  
## 使用されるオブジェクトとインターフェイス  
 次の図に、インプレース アクティブ化の作成に使用されるオブジェクトを示します。  
  
 ![埋め込み先編集の有効化エディター](~/docs/extensibility/media/vsinplaceactivationeditor.gif "vsInPlaceActivationEditor")  
インプレース アクティブ化エディター  
  
> [!NOTE]
>  この図のオブジェクトのうち、標準エディターの作成に必要なのは `CYourEditorFactory` オブジェクトのみです。 カスタム エディターを作成する場合は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> を実装する必要はありません。エディター独自のプライベートの永続化メカニズムを備えることになる可能性があるからです。 詳細については、「[カスタム エディターとデザイナーを作成します。](../extensibility/creating-custom-editors-and-designers.md)」を参照してください。  
  
 インプレース アクティブ化エディターを作成するために実装されているすべてのインターフェイスが、単一の `CYourEditorDocument` オブジェクトに示されていますが、この構成ではドキュメント データを単一のビューにのみ表示できます。 ドキュメント データを複数のビューに表示する方法の詳細については、「[複数のドキュメント ビューをサポートします。](../extensibility/supporting-multiple-document-views.md)」を参照してください。  
  
|インターフェイス|オブジェクトの型|使用|  
|--------------|--------------|--------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>|表示|<xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> サービスを使用することで、インプレース VSPackage オブジェクトは IDE に完全に統合されたコンポーネントとして動作できるようにします。 このサービスは、オブジェクトのメニューとツール バーとコマンドを IDE に統合し、状態変化の通知を発行します。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>|表示|埋め込みオブジェクトがコンテナーに基本的な機能を提供し、コンテナーと通信するための主要な手段です。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>|表示|インプレース オブジェクトのアクティブ化と非アクティブ化を管理し、インプレース オブジェクトのどのくらいの部分を表示するかを決定します。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceObject>|表示|インプレース オブジェクト、関連付けられているアプリケーションの最も外側のフレーム ウィンドウ、および埋め込みオブジェクトが含まれているアプリケーションのドキュメント ウィンドウの間における、通信の直接的なチャネルとなります。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>|表示|ActiveX オブジェクトを実装します。 ドキュメント データとビューを分離する <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> と `T:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView` のメソッドが IDE では使用されないことに注意してください。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|表示\/データ|ドキュメント データ オブジェクトまたはドキュメント ビュー オブジェクトのいずれか、あるいはその両方がコマンドの処理に参加できるようにします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|表示|ステータス バーを更新できるようにします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|表示|ツールボックスに項目を追加できるようにします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|データ|編集したファイルに変更の通知を送信します。 \(このインターフェイスは省略可能です\)。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|データ|ファイルの種類に対して名前を付けて保存機能を有効にするために使用します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|データ|ドキュメントの永続性を有効にします。 読み取り専用ファイルの場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SetDocDataReadOnly%2A> を呼び出して、読み取り専用ファイルであることを示す "ロック" アイコンを表示します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|データ|ドキュメント データへの変更を無視するかどうかを決定します。|