---
title: カスタム エディターでドキュメント データとドキュメントの表示 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6df543f832fa85ea6d74fc2846355fbf9deab912
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535299"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>カスタム エディターでのドキュメント データとドキュメント ビュー
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ドキュメント データとカスタム エディターでドキュメント ビュー](https://docs.microsoft.com/visualstudio/extensibility/document-data-and-document-view-in-custom-editors)します。  
  
カスタム エディターは、2 つの部分で構成されています。 ドキュメントのデータ オブジェクトとドキュメント ビュー オブジェクト。 名前からわかるように、ドキュメント データ オブジェクトが表示されるテキスト データを表すし、ドキュメント ビュー オブジェクト (または"view") は、ドキュメント データ オブジェクトを表示するための 1 つまたは複数の windows を表します。  
  
## <a name="document-data-object"></a>ドキュメント データ オブジェクト  
 ドキュメント データ オブジェクトは、テキスト バッファー内のテキストのデータ表現です。 これはドキュメントのテキストとその他の情報を格納、ドキュメントの永続化を処理し、データの複数のビューを使用する COM オブジェクト。 詳細については、次のトピックを参照してください。  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> [Windows ドキュメント](../extensibility/internals/document-windows.md)します。  
  
 カスタム エディターとデザイナーを使用することを選択できる、<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>オブジェクトまたは独自のカスタムのバッファー。 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 標準エディターの簡略化された埋め込みモデルに依存して、複数のビューをサポートし、複数のビューの管理に使用されるイベント インターフェイスを提供します。  
  
## <a name="document-view-object"></a>ドキュメント ビュー オブジェクト  
 コードとその他のテキストを表示するウィンドウがドキュメントと呼ばれる表示または表示します。 エディターを作成するときに、1 つのウィンドウに表示されるテキストを 1 つのビュー、または複数のビューで、複数のウィンドウに表示されるテキストのいずれかを選択できます。 選択は、アプリケーションによって異なります。 たとえば、サイド バイ サイドで編集する場合は、複数のビューを選択します。 それぞれのビューは、統合開発環境での (IDE) ドキュメント テーブル (RDT) を実行しているエントリに関連付けられます。 表示ウィンドウは、プロジェクトに属するまたは<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>オブジェクト。  
  
 エディターでは、ドキュメント データ オブジェクトの複数のビューをサポートする場合は、ドキュメント データとドキュメント ビュー オブジェクトを区切る必要があります。 それ以外の場合、グループ化できます。 詳細については、次を参照してください。 [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md)します。  
  
 IDE では、実行中のドキュメント テーブルの各エントリのアイテム識別子 (ItemID) を照合して (たとえば、ドキュメントを含むソリューションが閉じられたときに) イベントに関するビューを通知します。 詳細については、これは、次を参照してください。[を実行しているドキュメント テーブル](../extensibility/internals/running-document-table.md)します。  
  
 カスタム エディターのビューを作成するための 2 つのオプションがあります。 1 つは、インプレース アクティブ化モデル、ビューが ActiveX コントロールまたはドキュメントのデータ オブジェクトを使用してウィンドウでホストされている場所です。 2 つ目は、ビューがによってホストされている、簡略化された埋め込みモデル[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]と<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>ウィンドウのコマンドを処理するために実装されます。 インプレース アクティブ化モデルについては、次を参照してください。[インプレース アクティブ化](../misc/in-place-activation.md)します。 簡略化された埋め込みモデルについては、次を参照してください。[簡略化された埋め込み](../extensibility/simplified-embedding.md)します。  
  
## <a name="see-also"></a>関連項目  
 [複数のドキュメント ビューのサポート](../extensibility/supporting-multiple-document-views.md)   
 [簡略化された埋め込み](../extensibility/simplified-embedding.md)   
 [方法: ビュー ドキュメント データへのアタッチ](../extensibility/how-to-attach-views-to-document-data.md)   
 [ドキュメント ロック ホルダーの管理](../extensibility/document-lock-holder-management.md)   
 [1 つと複数タブのビュー](../extensibility/single-and-multi-tab-views.md)   
 [標準のドキュメントを保存しています](../extensibility/internals/saving-a-standard-document.md)   
 [永続化と実行の Document テーブル](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [開くエディター、プロジェクト内のファイルの決定](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [エディター ファクトリ](../extensibility/editor-factories.md)

