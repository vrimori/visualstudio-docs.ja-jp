---
title: 複数のドキュメント ビューのサポート |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e55eed8ffd2651ced96f192972127e710a565eaa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53830730"
---
# <a name="supporting-multiple-document-views"></a>複数のドキュメント ビューのサポート
エディター用の個別のドキュメント データとドキュメント ビュー オブジェクトを作成して、ドキュメントの 1 つ以上のビューを行うことができます。 場合によっては便利ですが、追加のドキュメント ビューは次のとおりです。  
  
- 新しいウィンドウのサポート:エディターで開いているウィンドウを既に持っているユーザーが選択して、新しいウィンドウを開けるように、同じ型の 2 つ以上のビューを提供する、エディターが必要な**新しいウィンドウ**コマンドから、**ウィンドウ**メニュー。  
  
- フォームおよびコードのサポートを参照してください。さまざまな種類のビューを提供するエディターとして使用します。 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]、たとえば、フォーム ビューとコード ビューの両方を提供します。  
  
  詳細については、Visual Studio パッケージ テンプレートによって作成されたカスタム エディターのプロジェクトで EditorFactory.cs ファイル CreateEditorInstance プロシージャを参照してください。 このプロジェクトの詳細については、次を参照してください。[チュートリアル。カスタム エディターを作成する](../extensibility/walkthrough-creating-a-custom-editor.md)します。  
  
## <a name="synchronizing-views"></a>ビューの同期  
 複数のビューを実装するときに、ドキュメント データ オブジェクトは、すべてのビューと、データの同期を維持する責任を負います。 インターフェイスを処理するイベントを使用する<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>データと複数のビューを同期します。  
  
 使用しない場合、<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>ドキュメント データ オブジェクトに加えられた変更を処理するために、独自のイベント システムを実装する必要があり、複数のビューを同期するオブジェクト。 さまざまなレベルの粒度は、複数のビューを最新に保つために使用できます。 最大細分度の設定は、1 つのビューに入力すると、他のビューはすぐに更新します。 最小の細分性でアクティブになるまで、他のビューは更新されません。  
  
## <a name="determining-whether-document-data-is-already-open"></a>ドキュメント データをかどうかを判断するは既に開かれています。  
 統合開発環境 (IDE) で実行中のドキュメント テーブル (RDT) は、ドキュメントのデータが次の図に示すように開いているかどうかを追跡するのに役立ちます。  
  
 ![DocDataView グラフィック](../extensibility/media/docdataview.gif "Docdataview")  
複数のビュー  
  
 独自のウィンドウ フレームに既定では、それぞれのビュー (ドキュメント ビュー オブジェクト) が含まれている (<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>)。 既に説明したように、ただし、ドキュメント データを表示できますで複数のビュー。 これを有効にするのには、Visual Studio は、対象のドキュメントがエディターで開いて既にかどうかを判断する RDT を確認します。 IDE を呼び出すと<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>でエディターを作成するには、NULL 以外の値が返される、`punkDocDataExisting`パラメーターは、ドキュメントが別のエディターで開いて既にことを示します。 詳細については、RDT 関数を参照してください[を実行しているドキュメント テーブル](../extensibility/internals/running-document-table.md)します。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>の実装で返されるドキュメント データ オブジェクトを調べます`punkDocDataExisting`ドキュメント データが、エディターの適切なかどうかを判断します。 (たとえば、HTML のデータのみが表示されます、HTML エディターによって。)適切な場合は、エディター ファクトリは、データの 2 番目のビューを提供する必要があります。 場合、`punkDocDataExisting`パラメーターが`NULL`、ことは、ドキュメント データ オブジェクトが別のエディターで開いているか、可能性の高い、ドキュメント データが既に別のビューと同じ、エディターで開かれています。 ドキュメントのデータが、エディター ファクトリがサポートされていない別のエディターで開いている場合は、エディター ファクトリを開く Visual Studio が失敗します。 詳細については、「[方法 :ドキュメント データをビューにアタッチ](../extensibility/how-to-attach-views-to-document-data.md)します。