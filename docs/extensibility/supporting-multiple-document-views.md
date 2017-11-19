---
title: "複数のドキュメント ビューをサポートする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 79b9224a16388dabbe2b68553e5c0d9bfff29519
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="supporting-multiple-document-views"></a>複数のドキュメント ビューをサポートします。
エディターの別のドキュメントのデータおよびドキュメント ビュー オブジェクトを作成することで、ドキュメントの 1 つ以上のビューを提供できます。 場合によっては便利ですが、追加のドキュメント ビューは次のとおりです。  
  
-   新しいウィンドウのサポート: 必要な同じ型での 2 つ以上のビューを提供するエディターを選択すると、エディターで開いているウィンドウを既に持っているユーザーが新しいウィンドウを開くことができます、**新しいウィンドウ**コマンドを**ウィンドウ**メニュー。  
  
-   フォームとコードの表示のサポート: さまざまな種類のビューを提供するエディターとして使用します。 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]、たとえば、フォーム ビューとコード ビューの両方を提供します。  
  
 詳細については、EditorFactory.cs プロジェクト ファイルで、カスタム エディター、Visual Studio パッケージ テンプレートによって作成された CreateEditorInstance プロシージャを参照してください。 このプロジェクトの詳細については、次を参照してください。[チュートリアル: カスタム エディターを作成する](../extensibility/walkthrough-creating-a-custom-editor.md)です。  
  
## <a name="synchronizing-views"></a>ビューの同期  
 複数のビューを実装するときに、ドキュメント データ オブジェクトは、データと同期されているすべてのビューを維持します。 イベントのインターフェイスを処理を行うこともできます<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>データで複数のビューを同期するためにします。  
  
 使用しない場合、<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>ドキュメント データ オブジェクトに加えられた変更を処理する、独自のイベント システムを実装する必要がありますし、複数のビューを同期するオブジェクト。 さまざまな詳細レベルを使用して、複数のビューを最新に保つことができます。 最大の粒度の設定、1 つのビューに入力すると、その他のビューは直ちに更新されます。 最小の粒度でアクティブになるまで、他のビューは更新されません。  
  
## <a name="determining-whether-document-data-is-already-open"></a>ドキュメント データをするかどうかを決めることが既に開かれています。  
 統合開発環境 (IDE) で実行中のドキュメント テーブル (RDT) は、ドキュメントのデータが次の図に示すように開いているかどうかを追跡することができます。  
  
 ![DocDataView グラフィック](../extensibility/media/docdataview.gif "Docdataview")  
複数のビュー  
  
 独自のウィンドウ フレームに既定では、それぞれのビュー (ドキュメント ビュー オブジェクト) が含まれている (<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>)。 既に説明したように、ただし、ドキュメント データを表示できます複数のビュー。 これを有効にするのには、Visual Studio は、問題のドキュメントがエディターで開いて既にかどうかを判断する RDT をチェックします。 IDE を呼び出すと<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>でエディターを作成するには、NULL 以外の値が返される、`punkDocDataExisting`パラメーターは、ドキュメントが既に別のエディターで開いていることを示します。 方法の詳細について、RDT 関数を参照してください[を実行しているドキュメント テーブル](../extensibility/internals/running-document-table.md)です。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>実装で返されるドキュメント データ オブジェクトを調べる`punkDocDataExisting`ドキュメントのデータが、エディターの適切なかどうかを判断します。 (たとえば、HTML のデータのみが表示されます、HTML エディターによって。)適切な場合は、エディター ファクトリは、データの 2 つ目のビューを指定する必要があります。 場合、`punkDocDataExisting`パラメーターではありません`NULL`、可能であれば、ドキュメント データ オブジェクトが別のエディターで開いているか、可能性の高い、ドキュメント データが既に別のビューと同じ、エディターで開きます。 ドキュメントのデータが、エディター ファクトリをサポートしない別のエディターで開いている場合は、Visual Studio は失敗を開くには、エディター ファクトリです。 詳細については、次を参照してください。[する方法: ドキュメント データへのアタッチ ビュー](../extensibility/how-to-attach-views-to-document-data.md)です。