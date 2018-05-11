---
title: カスタム エディターでドキュメントのデータおよびドキュメントを表示 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb445ca70ac74cf2601e9f1035549bb686fca798
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="document-data-and-document-view-in-custom-editors"></a>ドキュメント データとカスタム エディターでドキュメント ビュー
2 つの部分で構成されるカスタム エディター: ドキュメント データ オブジェクトとドキュメント ビュー オブジェクト。 名前からわかるように、ドキュメント データ オブジェクト テキスト データを表示するには、表しドキュメント ビュー オブジェクト (または"view") は、ドキュメント データ オブジェクトを表示するための 1 つまたは複数の windows を表します。  
  
## <a name="document-data-object"></a>ドキュメント データ オブジェクト  
 ドキュメント データ オブジェクトは、テキスト バッファー内のテキストのデータ表現です。 これは、ドキュメントのテキストとその他の情報を格納、ドキュメントの永続化を処理し、データの複数のビューを有効化する COM オブジェクトです。 詳細については、次のトピックを参照してください。  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> および[ドキュメント ウィンドウ](../extensibility/internals/document-windows.md)します。  
  
 カスタム エディターおよびデザイナーを使用することを選択できます、<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>オブジェクトまたは独自のカスタムのバッファー。 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 標準エディターの簡略化された埋め込みモデルに依存して、複数のビューをサポートおよびの複数のビューの管理に使用されるイベント インターフェイスを提供します。  
  
## <a name="document-view-object"></a>ドキュメント ビュー オブジェクト  
 コードおよびその他のテキストを表示するウィンドウがドキュメントと呼ばれるビューまたはビュー。 エディターを作成するときに、1 つのウィンドウでテキストを表示する、1 つのビューまたは複数のウィンドウでテキストを表示する複数のビューのいずれかを選択できます。 選択は、アプリケーションによって異なります。 たとえば、サイド バイ サイドで編集する場合は、複数のビューを選択します。 各ビューは、統合開発環境での (IDE) document テーブル (RDT) を実行しているエントリに関連付けられます。 ビューのウィンドウがプロジェクトに属している、または<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>オブジェクト。  
  
 エディターでは、ドキュメント データ オブジェクトの複数のビューをサポートする場合は、ドキュメント データおよびドキュメント ビュー オブジェクトを区切る必要があります。 それ以外の場合、グループ化できます。 詳細については、次を参照してください。[複数ドキュメントのビューをサポートする](../extensibility/supporting-multiple-document-views.md)です。  
  
 IDE では、実行中のドキュメント テーブル内の各エントリのアイテム識別子 (ItemID) を照合することで (たとえば、ドキュメントを含むソリューションが閉じられたときなど) のイベントに関するビューを通知します。 詳細については、次を参照してください。[を実行しているドキュメント テーブル](../extensibility/internals/running-document-table.md)です。  
  
 カスタム エディターのビューを作成するための 2 つのオプションがあります。 1 つは、インプレース アクティブ化モデル、ビューが ActiveX コントロールまたはドキュメント データ オブジェクトを使用して、ウィンドウでホストされている場所です。 2 つ目は、ビューがによってホストされている場所の簡易埋め込みモデル[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]と<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>ウィンドウ コマンドを処理するために実装がします。 インプレース アクティブ化モデルの詳細については、次を参照してください。 [、インプレース アクティブ化](../extensibility/in-place-activation.md)です。 簡略化された埋め込みモデルについては、次を参照してください。[簡略化された埋め込み](../extensibility/simplified-embedding.md)です。  
  
## <a name="see-also"></a>関連項目  
 [複数のドキュメント ビューをサポートします。](../extensibility/supporting-multiple-document-views.md)   
 [埋め込み簡素化されます。](../extensibility/simplified-embedding.md)   
 [方法: 添付ドキュメント データへのビュー](../extensibility/how-to-attach-views-to-document-data.md)   
 [ドキュメントのロック所有者の管理](../extensibility/document-lock-holder-management.md)   
 [単一サブネットおよびマルチ タブのビュー](../extensibility/single-and-multi-tab-views.md)   
 [標準的なドキュメントの保存](../extensibility/internals/saving-a-standard-document.md)   
 [永続化と実行中のドキュメント テーブル](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [どのエディターが開き、プロジェクトのファイルを決定します。](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [エディター ファクトリ](../extensibility/editor-factories.md)