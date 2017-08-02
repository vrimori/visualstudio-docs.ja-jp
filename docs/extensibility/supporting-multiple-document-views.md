---
title: "複数のドキュメント ビューをサポートします。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] カスタム - 複数のドキュメント ビュー"
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# 複数のドキュメント ビューをサポートします。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

エディターに別のドキュメント データとドキュメントのビュー オブジェクトを作成してドキュメントの複数のビューを提供できます。  追加のドキュメントのビューが便利の例を次に示します。:  
  
-   新しいウィンドウのサポート : エディターで既に開いているウィンドウを持つユーザーが ENT1ENT \[入力\] メニューの  **新規ウィンドウ**  のコマンドを使用して新しいウィンドウを開くことができるようにエディターに同じ型の複数のビューを提供する必要があります。  
  
-   フォーム ビューとコードのサポート : エディターのさまざまな型のビューを提供する必要があります。  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] はフォーム ビューとコード ビューの両方が用意されています。  
  
 この詳細についてはVisual Studio パッケージのテンプレートで作成されたカスタム エディターのプロジェクトの EditorFactory.cs ファイルの CreateEditorInstance の手順を参照してください。  このプロジェクトの詳細については[チュートリアル: カスタム エディターの作成](../extensibility/walkthrough-creating-a-custom-editor.md) を参照してください。  
  
## ビューの同期  
 複数のビューを実行するとドキュメント データ オブジェクトはすべてのビュー データを同期するために使用します。  データを複数のビューを同期するために <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> のイベント処理のインターフェイスを使用できます。  
  
 同期の複数のビューに <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> のオブジェクトを使用して行われるドキュメント データ オブジェクトに対する変更を処理する独自のイベント システムを実装する必要があります。  複数のビューを最新の状態に保つために次のレベルを使用できます。  最大次の設定では1 種類のビューを作成他のビューが直ちに更新されます。  最小の単位によって他のビューがアクティブになるまで更新されません。  
  
## ドキュメント データが開いているかどうかを判断します  
 ドキュメントのデータが既に開かれている \(IDE\) かどうかを次の図に示すように統合開発環境のヘルプ トラックの連続したドキュメントのテーブル \(RDT\)。  
  
 ![DocDataView グラフィック](~/extensibility/media/docdataview.gif "Docdataview")  
複数のビュー  
  
 既定ではドキュメントのビュービュー \(オブジェクト\) は独自のウィンドウ フレーム \(\)<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> に含まれています。  ドキュメント データが既に説明したように複数のビューで表示できます。  これを実現するにはそのドキュメントが既にエディターで開いているかどうかを調べます。RDT を確認します。  エディターを作成するにはIDE を <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> を呼び出すとき `punkDocDataExisting` のパラメーターで返される以外の値はドキュメントが既に別のエディターで開かれていることを示します。  詳細についてはRDT がどのように機能するか[実行中のドキュメント テーブル](../extensibility/internals/running-document-table.md) を参照してください。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> の実装ではドキュメント データのエディターに適しているかどうかを確認するに `punkDocDataExisting` とドキュメント データ オブジェクトを調べます。  \(HTML のデータのみの HTML エディターによって表示されます\)。必要に応じてエディターのファクトリはデータに 2 番目のビューを提供する必要があります。  `punkDocDataExisting` のパラメーターであるが `NULL`ドキュメントが既に同じデータの異なるビュー エディターで開いているドキュメントデータ オブジェクトが別のエディターで開かれているまたはです。より高いできるか。  ドキュメント データがエディターのファクトリでサポートされていない別のエディターで開かれている場合エディターのファクトリを開きます。  詳細については、「[方法: データを文書化するビューのアタッチ](../extensibility/how-to-attach-views-to-document-data.md)」を参照してください。