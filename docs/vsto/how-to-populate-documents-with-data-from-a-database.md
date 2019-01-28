---
title: '方法: データベースからデータをドキュメントに読み込む'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents, populating with data
- data, adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f1522b2567c05a9c3a61091813a8b5e18315433f
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863449"
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>方法: データベースからデータをドキュメントに読み込む

Microsoft Office のドキュメント レベルのプロジェクトでは、Windows フォーム プロジェクトでデータにアクセスする場合と同じようにデータにアクセスできます。 同じツールとコードを使用してデータベースからソリューションにデータを読み込むことができ、Windows フォーム コントロールを使用してデータを表示できます。

また、ホスト コントロールを使用してデータを表示することもできます。 ホスト コントロールは、イベントおよびデータ バインディングの機能が強化された Microsoft Office Word のネイティブ オブジェクトです。 詳細については、次を参照してください。[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)します。

[!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

次の例は、デザイナーを使用してドキュメント レベルのプロジェクトにデータ バインド コントロールを追加する方法を示しています。 実行時に VSTO アドイン プロジェクトでデータ バインド コントロールを追加する方法の例は、次を参照してください。[チュートリアル。VSTO アドイン プロジェクトでの単純データ バインディング](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)します。

![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。 [Word 2007 コンテンツへのデータのバインドは、Office system (3.0) の Visual Studio ツールの使用を制御](http://go.microsoft.com/fwlink/?LinkId=136785)します。

## <a name="add-a-control-to-a-document-at-design-time"></a>デザイン時にドキュメントにコントロールを追加します。

### <a name="to-populate-a-document-with-data-from-a-database"></a>データベースからドキュメントにデータを読み込むには

1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で Word のドキュメント レベルのプロジェクトを開き、ドキュメントをデザイナーで開きます。

2.  開く、**データ ソース**ウィンドウをデータベースからデータ ソースを作成します。 詳細については、次を参照してください。[新しい接続を追加](../data-tools/add-new-connections.md)します。

3.  目的のフィールドをドラッグして、**データ ソース**ドキュメント ウィンドウ。

コンテンツ コントロールが文書に追加されます。 コンテンツ コントロールの種類は、選択したフィールドのデータ型によって異なります。 詳細については、次を参照してください。[コンテンツ コントロール](../vsto/content-controls.md)します。

内のデータ フィールドを選択して別のコントロールを追加することができます、**データソース**ウィンドウとドロップダウン リストから別のコントロールを選択します。

## <a name="objects-in-the-project"></a>プロジェクト内のオブジェクト

プロジェクトには、コントロールに加えて、データに関連する以下のオブジェクトも自動的に追加されます。

-   データベース内の接続したデータ テーブルをカプセル化する型指定されたデータセット。 詳細については、次を参照してください。 [Visual Studio でのデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)します。

-   コントロールを型指定されたデータセットに接続する <xref:System.Windows.Forms.BindingSource>。 詳細については、次を参照してください。 [BindingSource コンポーネントの概要](/dotnet/framework/winforms/controls/bindingsource-component-overview)します。

-   型指定されたデータセットをデータベースに接続する TableAdapter。 詳細については、次を参照してください。[作成し、Tableadapter 構成](../data-tools/create-and-configure-tableadapters.md)します。

-   階層更新を有効にするデータセット内のテーブル アダプターを調整するために使用 TableAdapterManager します。 詳細については、次を参照してください。[階層更新](../data-tools/hierarchical-update.md)と[TableAdapterManager 参照](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference)します。

プロジェクトを実行すると、データ ソースの先頭のレコードがコントロールに表示されます。 <xref:System.Windows.Forms.BindingSource> を使用すると、ユーザーがレコードをスクロールできるようになります。

### <a name="to-scroll-through-the-records"></a>レコードをスクロールするには

-   <xref:System.Windows.Forms.BindingSource.MoveNext%2A> や <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> など、<xref:System.Windows.Forms.BindingSource> のメソッドを使用します。

型指定されたデータセットと、データベースに更新プログラムを送信する方法については、次を参照してください。[方法。ホスト コントロールからのデータでデータ ソースを更新](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)します。

## <a name="see-also"></a>関連項目

- [Office ソリューションでのコントロールにデータをバインドします。](../vsto/binding-data-to-controls-in-office-solutions.md)
- [新しいデータ ソースの追加](../data-tools/add-new-data-sources.md)
- [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [方法: オブジェクトからのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [方法: ホスト コントロールからのデータでデータ ソースを更新します。](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Office ソリューションの概要でのローカル データベース ファイルを使用します。](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource コンポーネントの概要](/dotnet/framework/winforms/controls/bindingsource-component-overview)