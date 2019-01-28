---
title: カスタム エディターでドキュメント データとドキュメントの表示 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f2deb04f14af93846b0b5a9e13dca14eb5ed710
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020153"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>ドキュメント データとカスタム エディターでドキュメント ビュー
カスタム エディターは、2 つの部分で構成されています。 ドキュメントのデータ オブジェクトとドキュメント ビュー オブジェクト。 名前からわかるように、ドキュメント データ オブジェクトを表示するテキスト データを表します。 同様に、ドキュメント ビュー オブジェクト (または"view") は、ドキュメント データ オブジェクトを表示するための 1 つまたは複数の windows を表します。  
  
## <a name="document-data-object"></a>ドキュメント データ オブジェクト  
 ドキュメント データ オブジェクトは、テキスト バッファー内のテキストのデータ表現です。 ドキュメントのテキストおよびその他の情報を格納する COM オブジェクトになります。 ドキュメント データ オブジェクトは、ドキュメントの永続化を処理し、そのデータの複数のビューを使用します。 詳細については、次のトピックを参照してください。  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> [Windows ドキュメント](../extensibility/internals/document-windows.md)します。  
  
 カスタム エディターとデザイナーを使用することを選択できる、<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>オブジェクトまたは独自のカスタムのバッファー。 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 標準エディターの簡略化された埋め込みモデルに依存して、複数のビューをサポートし、複数のビューの管理に使用されるイベント インターフェイスを提供します。  
  
## <a name="document-view-object"></a>ドキュメント ビュー オブジェクト  
 コードとその他のテキストを表示するウィンドウがドキュメントと呼ばれる表示または表示します。 エディターを作成するときに、いずれか 1 つのビューを 1 つのウィンドウに表示されるテキストを選択できます。 または、複数のビューで、複数のウィンドウに表示されるテキストを選択できます。 選択は、アプリケーションによって異なります。 たとえば、サイド バイ サイドで編集する場合は、複数のビューを選択します。 それぞれのビューは、統合開発環境での (IDE) ドキュメント テーブル (RDT) を実行しているエントリに関連付けられます。 表示ウィンドウは、プロジェクトに属するまたは<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>オブジェクト。  
  
 エディターでは、ドキュメント データ オブジェクトの複数のビューをサポートする場合は、ドキュメント データとドキュメント ビュー オブジェクトを区切る必要があります。 それ以外の場合、グループ化できます。 詳細については、次を参照してください。[ドキュメントの複数のビューをサポートして](../extensibility/supporting-multiple-document-views.md)します。  
  
 IDE では、実行中のドキュメント テーブルの各エントリのアイテム識別子 (ItemID) を照合して (たとえば、ドキュメントを含むソリューションが閉じられたときに) イベントに関するビューを通知します。 詳細については、これは、次を参照してください。 [document テーブルを実行している](../extensibility/internals/running-document-table.md)します。  
  
 カスタム エディターのビューを作成するための 2 つのオプションがあります。 1 つは、インプレース アクティブ化モデル、ビューが ActiveX コントロールまたはドキュメントのデータ オブジェクトを使用してウィンドウでホストされている場所です。 2 つ目は、ビューがによってホストされている、簡略化された埋め込みモデル[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]と<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>ウィンドウのコマンドを処理するために実装されます。 インプレース アクティブ化モデルについては、次を参照してください。[インプレース アクティブ化](../extensibility/in-place-activation.md)します。 簡略化された埋め込みモデルについては、次を参照してください。[簡略化された埋め込み](../extensibility/simplified-embedding.md)します。  
  
## <a name="see-also"></a>関連項目  
 [複数のドキュメント ビューをサポートします。](../extensibility/supporting-multiple-document-views.md)   
 [簡略化された埋め込み](../extensibility/simplified-embedding.md)   
 [方法: ドキュメント データへのビューをアタッチします。](../extensibility/how-to-attach-views-to-document-data.md)   
 [ドキュメント ロック ホルダーの管理](../extensibility/document-lock-holder-management.md)   
 [1 つと複数タブのビュー](../extensibility/single-and-multi-tab-views.md)   
 [標準のドキュメントを保存します。](../extensibility/internals/saving-a-standard-document.md)   
 [永続化と実行中のドキュメント テーブル](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [特定のエディターがプロジェクトでファイルを開きます](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [エディター ファクトリ](../extensibility/editor-factories.md)