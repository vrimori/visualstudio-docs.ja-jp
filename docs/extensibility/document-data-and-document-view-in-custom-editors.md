---
title: "ドキュメント データとカスタム エディターでドキュメント ビュー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] カスタムでは、データを文書化し、文書の表示"
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# ドキュメント データとカスタム エディターでドキュメント ビュー
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

2 つの部分で構成されるカスタム エディター: ドキュメントのデータ オブジェクトとドキュメント ビュー オブジェクト。 名前からわかるようには、ドキュメントのデータ オブジェクトが表示されるテキスト データを表す、ドキュメント ビュー オブジェクト \(または「ビュー」\) は、ドキュメントのデータ オブジェクトを表示するための 1 つまたは複数の windows を表します。  
  
## ドキュメント データ オブジェクト  
 ドキュメント データ オブジェクトは、テキスト バッファー内のテキストのデータ表現です。 これは、ドキュメントのテキストとその他の情報を格納、処理するドキュメントの持続性のデータの複数のビュー可能にする COM オブジェクト。 詳細については、次のトピックを参照してください。  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> および [ドキュメント ウィンドウ](../extensibility/internals/document-windows.md)。  
  
 カスタム エディターやデザイナーを選択できる、 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> オブジェクトまたは独自のカスタムのバッファー。<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 標準エディターの簡略化された埋め込みモデルに依存して、複数のビューをサポートしているおよびイベント インターフェイスを使用して複数のビューの管理を提供します。  
  
## ドキュメント ビュー オブジェクト  
 コードとその他のテキストを表示するウィンドウがドキュメントと呼ばれる表示または表示します。 エディターを作成するときに、1 つのウィンドウでテキストを表示する 1 つのビューまたは複数のビュー、複数のウィンドウでのテキストの表示のいずれかを選択できます。 選択は、アプリケーションによって異なります。 たとえば、サイド バイ サイドで編集する場合は、複数のビューを選択します。 各ビューは、統合開発環境での \(IDE\) の document テーブルの \(RDT\) を実行しているエントリに関連付けられます。 ビューのウィンドウが、プロジェクトに属するまたは <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> オブジェクトです。  
  
 エディターでは、ドキュメント データ オブジェクトの複数のビューをサポートする場合は、ドキュメント データおよびドキュメント ビューのオブジェクトを区切る必要があります。 それ以外の場合、グループ化できます。 詳細については、「[複数のドキュメント ビューをサポートします。](../extensibility/supporting-multiple-document-views.md)」を参照してください。  
  
 IDE では、実行中の document テーブルのエントリごとにアイテム識別子 \(ItemID\) を照合することで \(たとえば、ドキュメントを含むソリューションが閉じられたときなど\) のイベントに関するビューを通知します。 詳細については、「[実行中のドキュメント テーブル](../extensibility/internals/running-document-table.md)」を参照してください。  
  
 カスタム エディターのビューを作成するための 2 つのオプションがあります。 1 つは、インプレース アクティブ化モデル、ビューが ActiveX コントロール、またはドキュメントのデータ オブジェクトを使用して、ウィンドウでホストされている場所です。 2 番目は、ビューがによってホストされている場所、シンプルな埋め込みモデル [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] と <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> がウィンドウのコマンドを処理するために実装します。 インプレース アクティブ化モデルについては、次を参照してください。 [埋め込み先編集の有効化](../misc/in-place-activation.md)します。 簡略化された埋め込みモデルについては、次を参照してください。 [簡略化された埋め込み](../extensibility/simplified-embedding.md)します。  
  
## 参照  
 [複数のドキュメント ビューをサポートします。](../extensibility/supporting-multiple-document-views.md)   
 [簡略化された埋め込み](../extensibility/simplified-embedding.md)   
 [方法: データを文書化するビューのアタッチ](../extensibility/how-to-attach-views-to-document-data.md)   
 [ドキュメントのロック所有者の管理](../extensibility/document-lock-holder-management.md)   
 [単一および複数のタブ ビュー](../extensibility/single-and-multi-tab-views.md)   
 [標準的なドキュメントの保存](../extensibility/internals/saving-a-standard-document.md)   
 [永続化と実行中の Document テーブル](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [どのエディターが開き、プロジェクト内のファイルを決定します。](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [エディター ファクトリ](../extensibility/editor-factories.md)